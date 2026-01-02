# Runbook: Key Rotation (Vault-managed keys)

1. Generate new keys in Vault (per org policy)
2. Deploy encrypted credentials (systemd LoadCredentialEncrypted)
3. Restart decrypt/open units in maintenance window
4. Validate LUKS mappings and mounts
5. Validate no plaintext keys exist on disk
6. Produce evidence artifacts and update manifest checksums
