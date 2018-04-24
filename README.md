# icinga2-client

This role sets up a small Icinga 2 installation for remote monitoring.
The zones are automatically configured (parent zones + a global template zone).
Your nodename is automatically set to the inventory hostname.

A certificate is automatically requested and installed.

This role belongs to [icinga2-master](https://github.com/stuvusIT/icinga2-master).

## Requirements

Ubuntu

## Role Variables

| Name                            | Default/Required          | Description                                                             |
|---------------------------------|:-------------------------:|-------------------------------------------------------------------------|
| `icinga2_parent_zone`           | :heavy_check_mark:        | Name of the group of the parent zone                                    |
| `icinga2_ca_host`               | :heavy_check_mark:        | The host with the CA certificates, a certificate will be requested here |
| `icinga2_noagent_group`         | `icinga2-noagent`         | If a host is in this group, the client will not be deployed             |
| `icinga2_user`                  | `nagios`                  | User under which Icinga 2 is run                                        |
| `icinga2_group`                 | `nagios`                  | Group under which Icinga 2 is run                                       |
| `icinga2_plugin_dir`            | `/usr/lib/nagios/plugins` | Directory that contains the monitoring plugins                          |
| `icinga2_constants`             | `{}`                      | Dict of Icinga 2 constant strings                                       |
| `icinga2_icinga2_api_bind_host` | `0.0.0.0`                 | Host to bind on for API requests                                        |
| `icinga2_api_bind_port`         | `5665`                    | Port to bind on for API requests                                        |
| `icinga2_log_severity`          | `warning`                 | Severity for messages to be logged to the syslog                        |


## Example Playbook

```yml
- hosts: all
  roles:
  - icinga2-client
    icinga2_parent_zone: master
    icinga2_ca_host: icinga01
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Janne Heß](https://github.com/dasJ)
