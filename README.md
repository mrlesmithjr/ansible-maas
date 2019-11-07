# ansible-maas-regiond

[![contributing][contributing-img]](CONTRIBUTING.md)

1. [Overview](#overview)
1. [Description](#description)
1. [Requirements](#requirements)
1. [Setup](#setup)
1. [Role Variables](#role-variables)
1. [Playbook Example](#playbook-example)
1. [Dependencies](#dependencies)
1. [Limitations](#limitations)
1. [Development](#development)

## Overview

[MAAS](https://maas.io/docs/what-is-maas) is Metal As A Service. It lets you treat physical servers like virtual machines (instances)
in the cloud. Rather than having to manage each server individually, MAAS turns your bare metal
into an elastic cloud-like resource.

## Description

This role install and configure [MAAS Region Controller](https://maas.io/docs/region-controller).

## Requirements

| Type       | RAM  | CPU | Disk |
|------------|------|-----|------|
| PostgreSQL | 2048 | 2.0 | 20   |
| Regiond    | 2048 | 2.0 | 5    |


## Setup

Use `ansible-galaxy` or download the role in your `roles` directory.

## Role Variables

NB: PostgreSQL password can be supplied as unhashed string or MD5 one with username concatenated.

For example:
```shell
$ USER=maas PASSWORD=pwetPwet \
        echo md5$(echo -n "${USER}${PASSWORD}" | md5sum | awk '{print $1}')
```

```yaml
maas_users:
  admins:
    - username: foobar
      email: "foobar@{{ maas_dns.domain }}"
      # $ USER=maas PASSWORD=pwetPwet \
      #   echo md5$(echo -n "${USER}${PASSWORD}" | md5sum | awk '{print $1}')
      password: md5ee79bb3a790bb6c76f854e897eff29b5
```

## Playbook Example

Use default configuration, means that nothing will be done.

```yaml
- hosts: localhost
  roles:
    - ansible-maas-regiond
```

## Dependencies

None.

## Limitations

So far, this is compatible with Debian and derivatives.

## Development

Please read carefully CONTRIBUTING.md before making a merge request.

[contributing-img]: https://img.shields.io/badge/contributing--grey.svg

## Author Information

Forked from [mrlesmithjr/ansible-maas](https://github.com/mrlesmithjr/ansible-maas)
