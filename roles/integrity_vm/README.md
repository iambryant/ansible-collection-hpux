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

    integrity_vswitch_name: "vsw0"

The name of the default vswitch that vPars/VMs will use. Defaults to `vsw0`.

    integrity_vswitch_lan: "0"

The interface index to bind the vswitch to (e.g. lan0, lan1). Defaults to `0` for lan0.

    integrity_guests: []

A list of dictionaries defining the vPars/VMs to be created. Supports the following parameters:

| Parameter      | Type    | Required | Description                                                                     |
| :---           | :---    | :---     | :---                                                                            |
| `vm_name`      | String  | **Yes**  | The name of the VM. Will also be used as the logical volume name.               |
| `cpus`         | Integer | **Yes**  | The number of CPUs to assign to the VM.                                         |
| `ram_size`     | String  | **Yes**  | The size of RAM to assign to the VM (e.g. `"8G"`).                              |
| `vg_name`      | String  | **Yes**  | The volume group to store the VM disk on.                                       |
| `lv_size`      | Integer | **Yes**  | The size of the logical volume to use for the VM in MB (e.g. `65536` for 64GB). |
| `vswitch_name` | String  | **Yes**  | The virtual switch name to use for the VM.                                      |
| `mac_address`  | String  | No       | The specific MAC address to assign to the VM.                                   |
| `autoboot`     | Boolean | No       | Whether or not to automatically boot the VM on hypervisor startup.              |

## Dependencies

None.

## Example Playbook

    - hosts: all
      become: true
      vars:
        ansible_python_interpreter: /usr/local/bin/python3
      roles:
        - lpars.hpux.integrity_vm

## License

MIT

