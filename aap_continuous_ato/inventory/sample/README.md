# Sample Inventory

This directory provides an example host/group layout for:

- HAProxy edge
- AAP Controllers (HA)
- Private Hub (HA)
- EDA (HA)
- External PostgreSQL (HA)

## GovCloud / GCC High Notes
- Use private endpoints and private DNS zones where available
- Prefer mTLS for service-to-service calls where supported
- Store all API tokens and secrets in Ansible Vault or an external secrets manager

