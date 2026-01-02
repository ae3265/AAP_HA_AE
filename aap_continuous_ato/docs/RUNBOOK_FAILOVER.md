# Runbook: PostgreSQL Failover (HA)

1. Confirm Patroni health and leader
2. Validate HAProxy backend health
3. Trigger controlled switchover (preferred) or observe automatic failover
4. Validate AAP service connectivity
5. Collect evidence artifacts (runtime state + logs)
6. Record action in POA&M (if outage impacted controls)

This runbook is automated by `postgres_ha` validation and DR drill playbooks in this collection.
