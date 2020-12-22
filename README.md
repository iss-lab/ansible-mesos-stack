# Ansible Playbook to install a complete Apache Mesos stack


[![Donate](https://img.shields.io/liberapay/receives/AVENTER.svg?logo=liberapay)](https://liberapay.com/mesos)
[![Support Chat](https://img.shields.io/static/v1?label=Chat&message=Support&color=brightgreen)](https://riot.im/app/#/room/#support:matrix.aventer.biz)

This playbook deploys a full Apache Mesos stack. The access to mesos (agent and master) and marathon need credentials. The default one is "marathon:marathon".


## Requirements

- CentOS 7

## How to use

### Install the whole stack

```bash
ansible-playbook -i ../inventory/inventory/mesos plays/server-config.yaml
```

### Reconfigure DNS

```bash
ansible-playbook -i ../inventory/inventory/mesos plays/server-config.yaml --tags dns
```

### Reconfigure Weave

```bash
ansible-playbook -i ../inventory/inventory/mesos plays/server-config.yaml --tags weave
```

## Manager node


| Software version   | Role                              | Install type                       |
| ------------------ | :-------------------------------: | :--------------------------------: |
| Mesos 1.10.0       | Mesos Masters                     | RPM                                |
| Marathon 1.10.17   | Marathon masters                  | RPM                                |
| Zookeeper 3.8.5    | Zookeeper cluster                 | dependencies to Mesos/Marathon RPM |
| Mesos-DNS 0.7.0    | Service Discovery for Mesos Tasks | RPM                                |
| Metronome 0.6.30   | Schedule Server                   | JAVA dependencies to Marathon      |
| Nodeexporter 0.18.2| Metric Exporter                   | Binary

## Worker node

| Software version   | Role                              | Install type |
| ------------------ | :-------------------------------: | :----------: |
| Mesos 1.10.0       | Mesos Agent                       | RPM          |
| Docker 19.03.1-ce  | Docker engine                     | RPM          |
| Weave 2.6.0        | Container networking              | Docker image |
| Weavescope 1.11.3  | Container Management              | Docker image |
| DNSMasq 2          | Container DNS                     | RPM          |
| CAdavisor (deprecated)         | Docker engine monitoring          | Docker image |
| Rexray 0.11.4      | Persistant Storage                | RPM          |
| Nodeexporter 0.18.2| Metric Exporter                   | Binary
