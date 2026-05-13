# Ansible Role: Integrity VM

This role installs HP-UX vPars and Integrity VM v6.5 as per HP's [documentation](https://support.hpe.com/hpesc/public/docDisplay?docId=a00050738en_us&docLocale=en_US)
and configures a default vswitch vsw0.

## Requirements

* **OS:** HP-UX 11i v3 (B.11.31) on Itanium (IA64).
* **Python:** Ansible requires Python 3. See the [HP-UX Porting and Archive Centre](http://hpux.connect.org.uk) for compatible Python packages.

## Role Variables

    hpux_sdux_server: ""

The network depot to install Ignite-UX from. Note: This variable is shared across all roles in this collection
to centralize package management.

    hpux_sdux_server_path: "/var/spool/sw"

The network depot path to install depots from. Defaults to `/var/spool/sw`. Note: This variable is shared across all roles
in this collection to centralize package management.

    vswitch_name: "vsw0"

The name of the default vswitch that vPars/VMs will use. Defaults to `vsw0`.

    vswitch_lan: "0"

The interface index to bind the vswitch to (e.g. lan0, lan1). Defaults to `0` for lan0.

## Dependencies

None.

## Example Playbook

    - hosts: integrity_vm
      become: true
      vars:
        ansible_python_interpreter: /usr/local/bin/python3
      roles:
        - lpars.hpux.integrity_vm

## License

MIT

