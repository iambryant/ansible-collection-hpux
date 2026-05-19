# Ansible Collection: HP-UX

[![CI](https://github.com/LPARS/ansible-collection-hpux/actions/workflows/ci.yml/badge.svg)](https://github.com/LPARS/ansible-collection-hpux/actions/workflows/ci.yml)

This collection includes roles for automating common tasks in HP-UX.

## Installation

You can include this collection in your requirements.yml like this:

```
collections:
  - name: lpars.hpux
    source: https://github.com/LPARS/ansible-collection-hpux
    type: git
```

## Requirements

* **OS:** HP-UX 11i v3 (B.11.31) on Itanium (IA64).
* **Python:** Ansible requires Python 3. See the [HP-UX Porting and Archive Centre](http://hpux.connect.org.uk)
for compatible Python packages.

## Included Roles

Roles included in this collection:

  - `lpars.hpux.ignite_ux` ([documentation](https://github.com/lpars/ansible-collection-hpux/blob/main/roles/ignite_ux/README.md))
  - `lpars.hpux.integrity_vm` ([documentation](https://github.com/lpars/ansible-collection-hpux/blob/main/roles/integrity_vm/README.md))
  - `lpars.hpux.ntp` ([documentation](https://github.com/lpars/ansible-collection-hpux/blob/main/roles/ntp/README.md))

## Usage

To see an example of this collection's usage, see: https://github.com/LPARS/hpux-dev-playbook.

## License

MIT
