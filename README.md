[![Build Status](https://travis-ci.org/bihealth/ansible-role-varfish-server.svg?branch=master)](https://travis-ci.org/bihealth/ansible-role-varfish-server)

# VarFish Server

Setup of VarFish server.

## Requirements

A PostgreSQL server (version >= 11) has to be setup independently.
You could use `bihealth.postgres_server`.

## Role Variables

See `defaults/main.yml` for all role variables and their documentation.

## Dependencies

- `bihealth.sodar_core_app`

## Example Playbook

```yaml
- hosts: servers
  vars:
    # bihealth.sodar_core_app ---------------------------------------------------------------------
    sodar_core_app_version: "v0.16.1"
    sodar_core_app_django_secret_key: "SOMESECRETKEYSOMESECRETKEYSOMESECRETKEYSOMESECRETKEY"
    sodar_core_app_superuser_password: "junkpass"
    # bihealth.ssl_certs --------------------------------------------------------------------------
    ssl_certs_certs:
      - name: varfish.example.com
    # bihealth.postgres_client --------------------------------------------------------------------
    postgres_client_host: 127.0.0.1
    postgres_client_db: varfish-test
    postgres_client_user: varfish-test
    postgres_client_password: varfish-test
  roles:
    - role: bihealth.varfish_server
```

## License

MIT

## Author Information

- Manuel Holtgrewe

Created with love at [Core Unit Bioinformatics (CUBI), Berlin Institute of Health (BIH)](https://www.cubi.bihealth.org).
