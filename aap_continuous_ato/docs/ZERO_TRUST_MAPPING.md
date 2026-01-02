# Zero Trust Overlay Mapping (NIST SP 800-207 → Implementation)

| ZT Concept | In This Architecture | NIST 800-53 Touchpoints |
|---|---|---|
| Policy Enforcement Point (PEP) | HAProxy (SNI, TLS re-encrypt, 443-only) | SC-7, SC-8, SC-13 |
| Policy Engine / Continuous Evaluation | OPA (design-time + runtime), Drift Detect | CA-7, CM-2, SI-4 |
| Strong Identity | (Environment-specific: SSO/MFA) | IA-2, IA-5, AC-2 |
| Least Privilege | RBAC, segmented FQDNs | AC-6, AC-3 |
| Data Protection | LUKS encryption, Vault keys, PITR | SC-28, SC-12, CP-9 |
| Visibility & Analytics | Prometheus/Grafana + Evidence Chain | AU-6, SI-4 |

