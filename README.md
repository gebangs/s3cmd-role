S3cmd Role
=========

Installs and configures s3cmd.

**Security Notice**: This role handles sensitive AWS credentials. Always use Ansible Vault or other secure methods to store credentials. Never commit plaintext credentials to version control.

Requirements
------------

- Ansible 2.9+
- Target systems must be Debian/Ubuntu-based (uses apt package manager)
- AWS credentials (access key and secret key) must be provided securely via Ansible Vault

Role Variables
--------------

### Required Variables (must be set via Ansible Vault)

- `s3cmd_access_key`: AWS Access Key ID
- `s3cmd_secret_key`: AWS Secret Access Key

### Optional Variables

- `s3cmd_version`: Specific version of s3cmd to install (default: "", installs latest)
- `s3cmd_authorized_group`: Group name for s3cmd access control (default: s3cmd)
- `s3cmd_authorized_user`: User to add to the authorized group (default: "")
- `s3cmd_gpg_passphrase`: GPG passphrase for encryption (store securely)

### Configuration Variables

All other s3cmd configuration options are available. See `defaults/main.yml` for full list.
Key options include:
- `s3cmd_use_https`: Enable HTTPS (default: True)
- `s3cmd_bucket_location`: Default bucket location (default: US)
- `s3cmd_host_base`: S3 endpoint (default: s3.amazonaws.com)

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      vars_files:
        - vault/s3cmd_credentials.yml  # Encrypted with Ansible Vault
      roles:
         - role: s3cmd-role

Example vault file (encrypt with `ansible-vault encrypt vault/s3cmd_credentials.yml`):

    ---
    s3cmd_access_key: "AKIAIOSFODNN7EXAMPLE"
    s3cmd_secret_key: "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY"

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
