# RMF / NIST 800-53 Mapping (Control → Automation → Evidence)

> This table is a *starting baseline*. Tailor control applicability and parameters to your environment.

| NIST 800-53 Control | Automation Implementation (Role/Play) | Evidence Produced |
|---|---|---|
| CA-7 Continuous Monitoring | `playbooks/conmon.yml` + `opa_*` + `drift_detect` | findings JSON, Prom metrics, Grafana dashboard |
| CM-2 Baseline Configuration | `drift_detect` | drift diff JSON, correlated findings |
| SC-12 Key Management | `credstore_secure` + Vault integration (env-specific) | credstore validation outputs, attachment JSON |
| SC-13 Cryptographic Protection | `haproxy_tls`, LUKS, TLS policies | OpenSCAP results, runtime OPA denies (if any) |
| SC-28 Protection of Information at Rest | `postgres_ha` + `credstore_secure` | mapper/mount checks, OpenSCAP rules |
| CP-9 System Backup | `postgres_pitr` | basebackup timer evidence, WAL config |
| CP-10 Recovery | `postgres_dr_drills` | DR drill logs, PITR validation evidence |
| AU-6 Audit Review | auditd + evidence export | OpenSCAP auditd rules, runtime snapshots |
| SI-4 Monitoring | Prometheus/Grafana + OPA runtime | metrics + deny findings |

## Evidence Chain Integrity
- `bundle_manifest-<run_id>.json` enumerates artifacts and SHA-256
- POA&M narratives include:
  - per-POA&M attachment filename + sha256
  - manifest filename + sha256

