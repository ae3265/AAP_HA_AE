# ATO Overview (Assessor Friendly)

## What is Authorized?
A highly available deployment of Ansible Automation Platform (AAP) on RHEL 9 with external PostgreSQL, protected by a Zero Trust-aligned ingress and a Continuous Monitoring/Continuous ATO pipeline.

## What is Continuously Enforced?
- DISA STIG alignment using OpenSCAP scans
- Policy enforcement using OPA (design-time and runtime gates)
- Drift detection against declared desired state
- Automated evidence generation and integrity verification (SHA-256 manifests)
- Automated POA&M lifecycle actions and artifact uploads to eMASS

## What Evidence is Produced?
- OpenSCAP HTML/XML/JSON
- Runtime state snapshots
- Drift diffs and correlated findings
- Per-POA&M attachment JSON (bounded) with checksums
- Bundle manifests listing all artifacts + SHA-256
- Prometheus-exported compliance metrics and Grafana dashboards

## How to Validate Quickly
1. Run `playbooks/validate_compliance.yml`
2. Inspect `bundle_manifest-<run_id>.json` and verify checksums
3. Confirm correlated POA&M narratives contain attachment + manifest SHA-256
4. Review eMASS artifact uploads and POA&M updates (or dry-run plan)

