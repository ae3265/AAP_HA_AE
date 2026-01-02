# AAP Continuous ATO Collection

This collection provides a reference implementation to deploy **Ansible Automation Platform (AAP)** on **RHEL 9** with:

- High Availability baseline
- Zero Trust-aligned ingress on **443-only** with SNI and TLS re-encrypt
- External PostgreSQL HA with replication, automated failover, WAL + PITR
- OpenSCAP DISA STIG scans (RHEL 9) and OPA policy gates (design-time + runtime)
- Continuous drift detection
- eMASS automation: POA&M create/update/close + milestones, and artifact uploads
- Audit-grade evidence chain: per-POA&M attachments, bundle manifests, SHA-256 integrity

> **Note:** This package is a *framework/baseline* intended for controlled environments.
> Replace the placeholder URLs, FQDNs, and tenant endpoints in `group_vars` and docs.

## Quick Start

Install the collection tarball:

```bash
ansible-galaxy collection install platform-aap_continuous_ato-1.0.0.tar.gz --force
```

Run the Continuous Monitoring (ConMon) pipeline (dry-run by default):

```bash
ansible-playbook platform/aap_continuous_ato/playbooks/conmon.yml -e conmon_dry_run=true
```

## Docs

- `docs/ARCHITECTURE.md` — one-page architecture (ASCII + Mermaid)
- `docs/ATO_OVERVIEW.md` — assessor-friendly summary
- `docs/RMF_MAPPING.md` — NIST 800-53 mappings (control → role → evidence)
- `docs/ZERO_TRUST_MAPPING.md` — NIST 800-207 overlay mapping
- `docs/AUDITOR_GUIDE.md` — how to validate evidence and integrity chain

## Sample Inventory

See `inventory/sample/` for example hosts/groups and vars (GovCloud/GCC High notes included).

## License

Apache-2.0
