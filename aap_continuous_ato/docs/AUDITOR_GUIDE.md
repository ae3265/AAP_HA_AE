# Auditor Guide

## What to Look For
- OpenSCAP report: `openscap/report.html` (within evidence bundle)
- Bundle manifest: `bundle_manifest-<run_id>.json`
- Correlated findings: `findings-<run_id>.json`
- Per-POA&M child attachments (JSON) inside `emass_poam_attachments_bundle-<run_id>.zip`

## Integrity Verification
1. Compute SHA-256 for each file listed in the bundle manifest
2. Compare to the manifest `entries[].sha256`
3. Confirm POA&M narrative includes:
   - attachment filename + sha256
   - manifest filename + sha256

## Continuous Monitoring Signals
- Prometheus metrics:
  - `aap_conmon_opa_denies`
  - `aap_conmon_drift_changes`
  - `aap_conmon_openscap_high`
  - POA&M counters

## Dry-Run Mode
If `conmon_dry_run=true`, API writes are disabled. The run produces a plan artifact (what would be created/updated/closed).

