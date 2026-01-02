# Runbook: PITR (Point-in-Time Recovery)

1. Confirm WAL archive availability
2. Identify restore target timestamp and LSN
3. Restore base backup to staging restore host
4. Apply WAL to target time
5. Validate DB consistency and application queries
6. Promote restored instance if required
7. Produce evidence bundle and update eMASS artifacts/POA&M as needed
