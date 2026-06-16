# Ansible Collection: HP-UX

[![CI](https://github.com/iambryant/ansible-collection-hpux/actions/workflows/ci.yml/badge.svg)](https://github.com/iambryant/ansible-collection-hpux/actions/workflows/ci.yml)

This collection includes roles for automating common tasks in HP-UX.

## Installation

You can include this collection in your `requirements.yml` like this:

```
collections:
  - name: iambryant.hpux
    source: https://github.com/iambryant/ansible-collection-hpux
    type: git
```

## Requirements

* **Python:** Ansible requires Python, which HP-UX does not include by default. See the [HP-UX Porting and Archive Centre](http://hpux.connect.org.uk)
for compatible Python packages.

## Included Roles

  - `iambryant.hpux.ignite_ux` ([documentation](https://github.com/iambryant/ansible-collection-hpux/blob/main/roles/ignite_ux/README.md))
  - `iambryant.hpux.integrity_vm` ([documentation](https://github.com/iambryant/ansible-collection-hpux/blob/main/roles/integrity_vm/README.md))
  - `iambryant.hpux.ntp` ([documentation](https://github.com/iambryant/ansible-collection-hpux/blob/main/roles/ntp/README.md))

## Usage

To see an example of this collection's usage, see: https://github.com/iambryant/hpux-dev-playbook.

## License

MIT
