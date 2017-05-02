# Ansible Role: freetds

An ansible role to install freetds.

It compiles and installs the branch `branch-1_00` from github.

## Requirements

> This role has been tested on `Ubuntu 16.04` and `Ubuntu 16.10` only.

## Variables

- `freetds_global_config_items`: a list of name value pairs for the global configuration section.
  - Default:
    ```yaml
      - { name: "tds version", value: "auto" }
      - { name: "text size", value: "64512" }
    ```

- `freetds_server_config_items`: server configuration items. see next section.
  - Default: `[]`

### Server Configuration Items Definition

`freetds_server_config_items` is is a dictionary of `servers` and each `server a list of dictionaries that should conform to the following definition.

- `name`: the configuration name. e.g. `inventory`
  - **Required**

- `value`: the configuration value. e.g `etc/ansible/hosts`.
  - **Required**


## Usage Example

```yaml
- hosts: all
  vars:
    freetds_global_config_items:
      - { name: "tds version", value: "7.4" }
    freetds_server_config_items:
      MySQLServer:
        - { name: "host", value: "server.domain.com" }
        - { name: "port", value: "1433" }
        - { name: "tds version", value: "7.0" }
  roles:
    - thedumbtechguy.freetds
```

## License

MIT / BSD

## Author Information

This role was created by [TheDumbTechGuy](https://github.com/thedumbtechguy) ( [twitter](https://twitter.com/frostymarvelous) | [blog](https://thedumbtechguy.blogspot.com) | [galaxy](https://galaxy.ansible.com/thedumbtechguy/) )

## Credits