# Security Policy

This repository does NOT store plaintext credentials, private keys, or database dumps.

## Secret handling rules

Do NOT commit:
- Passwords or API tokens
- SSH private keys
- Database dumps
- Screenshots containing credentials

## Approved methods

- GitHub Secrets (for GitHub Actions)
- External password manager or vault
- Encrypted files (only if absolutely necessary)

If a secret is accidentally committed:
1. Rotate the secret immediately
2. Remove the file from the repository
3. Rewrite history if required

Security is treated as a first-class concern in this lab.
