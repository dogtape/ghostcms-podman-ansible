# Dogtape Ghostcms Ansible Project

## How to use

1. Copy `inventory/hosts.yml.example` to `inventory/hosts.yml` and edit how to connect to hosts
2. Create a vault password in `vault.pass`
3. Use ansible vault to encrypt db secrets. Place the encryped string in `inventory/group_vars/secrets_db.yml`. the command is `ansible-vault encrypt_string --vault-password-file vault.pass {{ value }} --name {{ var name }}`

| variable name in ansible | value                          |
|--------------------------|--------------------------------|
| db_root_password         | (generated password)           |
| db_password              | (generated password)           |

4. Follow [Ghost's Tinybird setup](https://docs.ghost.org/install/docker#get-tinybird-setup) and obtain `TINYBIRD_API_URL`, `TINYBIRD_WORKSPACE_ID`, `TINYBIRD_ADMIN_TOKEN`, and `TINYBIRD_TRACKER_TOKEN`.
5. Use ansible vault to encrypt tinybird configs. Place the encryped string in `inventory/group_vars/secrets_tinybird.yml`. the command is `ansible-vault encrypt_string --vault-password-file vault.pass {{ value }} --name {{ var name }}`

| variable name in ansible | value                              |
|--------------------------|------------------------------------|
| smtp_host                | (smtp host)                        |
| smtp_port                | (smtp TLS!!! port usually 465)     |
| smtp_auth_user           | (smtp auth user)                   |
| smtp_from                | '(display name)' <(sending email)> |
| smtp_auth_pass           | (smtp auth pass)                   |

4. Find an SMTP provider (or host your own) and obtain credentials.
5. Use ansible vault to encrypt SMTP credentials. Place the encryped string in `inventory/group_vars/secrets_smtp.yml`. the command is `ansible-vault encrypt_string --vault-password-file vault.pass {{ value }} --name {{ var name }}`

## Included content/ Directory Structure

The directory structure follows best practices recommended by the Ansible
community. Feel free to customize this template according to your specific
project requirements.

```shell
 ansible-project/
 |── .devcontainer/
 |    └── docker/
 |        └── devcontainer.json
 |    └── podman/
 |        └── devcontainer.json
 |    └── devcontainer.json
 |── .github/
 |    └── workflows/
 |        └── tests.yml
 |    └── ansible-code-bot.yml
 |── .vscode/
 |    └── extensions.json
 |── collections/
 |   └── requirements.yml
 |   └── ansible_collections/
 |       └── project_org/
 |           └── project_repo/
 |               └── README.md
 |               └── roles/sample_role/
 |                         └── README.md
 |                         └── tasks/main.yml
 |── inventory/
 |   |── hosts.yml
 |   |── argspec_validation_inventory.yml
 |   └── groups_vars/
 |   └── host_vars/
 |── ansible-navigator.yml
 |── ansible.cfg
 |── devfile.yaml
 |── linux_playbook.yml
 |── network_playbook.yml
 |── README.md
 |── site.yml
```

## Compatible with Ansible-lint

Tested with ansible-lint >=24.2.0 releases and the current development version
of ansible-core.
