# Ansible Role: Node Exporter

[![CI](https://github.com/DudeCalledBro/ansible-role-node_exporter/actions/workflows/ci.yml/badge.svg)](https://github.com/DudeCalledBro/ansible-role-node_exporter/actions/workflows/ci.yml)

This repository contains my ansible role for installing Prometheus Node Exporter with Docker. This role implements the basic Node Exporter, without any authorization or certificates. Please reffer to the Prometheus Node Exporter configuration page [here](https://github.com/prometheus/exporter-toolkit/blob/master/docs/web-configuration.md).

## Prerequisites

- Ensure you have Ansible installed (e.g. `pip3 install ansible`)
- Ensure Docker is installed on the target server (you may want to checkout my [ansible-docker-role](https://github.com/DudeCalledBro/ansible-role-docker))

## Role Variables

The default values for the variables are set in [defaults/main.yml](./defaults/main.yml)

```yaml
# Node Exporter Deployment Path, Owner and Group
node_exporter_path: /opt/node-exporter
node_exporter_file_owner: root
node_exporter_file_group: root

# Node Exporter Docker Container Configuration
node_expoter_image: prom/node-exporter:latest

node_exporter_commands: []
# node_exporter_commands:
# - "--collector.filesystem.fs-types-exclude=<value>"

node_exporter_mounts: []
# node_exporter_mounts:
# - <path_on_host>/tls.crt:/tls.crt
# - <path_on_host>/tls.key:/tls.key

node_exporter_webconfig: ""
# node_exporter_webconfig: |
#   tls_server_config:
#     cert_file: /tls.crt
#     key_file: /tls.key

# Node Exporter Connection Details (Verify)
node_exporter_host: localhost
node_exporter_port: 9100

```

```yaml
- hosts: all
  roles:
  - role: dudecalledbro.node_exporter
```

## License

Copyright © 2024 Niclas Spreng

Licensed under the [MIT license](LICENSE).
