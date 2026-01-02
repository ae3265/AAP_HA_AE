# ATO Architecture (One Page)

## System Boundary (Authorization Boundary)

```text
+----------------------------------------------------------------------------------+
|                            AUTHORIZATION BOUNDARY                                |
|                                                                                  |
|  RHEL 9 (FIPS)                                                                   |
|   - HAProxy (443-only, SNI routing, TLS re-encrypt)                              |
|   - AAP Controllers (HA)                                                         |
|   - Private Automation Hub (HA)                                                  |
|   - Event-Driven Automation (HA)                                                 |
|   - External PostgreSQL Cluster (HA)                                             |
|   - Continuous ATO Engine (OpenSCAP + OPA + Drift + Evidence + eMASS Sync)       |
+----------------------------------------------------------------------------------+
```

## Data Flows (High Level)

```mermaid
flowchart LR
  U[Users / CI] -->|443 TLS| LB[HAProxy (SNI, TLS Re-encrypt)]
  LB --> C[AAP Controllers (HA)]
  LB --> H[Private Hub (HA)]
  LB --> E[EDA (HA)]
  C -->|DB TLS| PG[(External PostgreSQL HA)]
  H -->|DB TLS| PG
  E -->|DB TLS| PG

  subgraph ConMon[Continuous ATO Engine]
    SCAP[OpenSCAP (DISA STIG RHEL9)] --> OPA[OPA Policy Gates]
    RT[Runtime State Collect] --> OPA
    DRIFT[Drift Detection] --> OPA
    OPA --> CORR[Noise Suppression / Correlation]
    CORR --> EVID[Evidence Bundles + Manifests (SHA-256)]
    EVID --> EMASS[eMASS Artifacts + POA&M Automation]
  end

  C --> ConMon
  H --> ConMon
  E --> ConMon
  PG --> ConMon
```

## Trust & Verification (Zero Trust Overlay)

- **Identity & Access:** least privilege, strong auth, continuous evaluation
- **Transport:** 443-only, TLS re-encrypt, SNI isolation per FQDN
- **Data:** encrypted at rest (LUKS), keys protected via systemd encrypted credentials + Vault, PITR validated
- **Telemetry:** Prometheus metrics, Grafana dashboards, audit evidence chain

