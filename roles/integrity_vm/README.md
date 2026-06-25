# Ansible Role: Integrity VM

This role installs HP-UX vPars and Integrity VM v6.5 as per HP's [documentation](https://support.hpe.com/hpesc/public/docDisplay?docId=a00050738en_us&docLocale=en_US)
and configures a default vswitch vsw0.

## Requirements

* **Python:** Ansible requires Python, which HP-UX does not include by default. See the [HP-UX Porting and Archive Centre](http://hpux.connect.org.uk)
for compatible Python packages.

## Role Variables

    hpux_staging_dir: "/var/tmp"

The temporary directory to copy `.depot` files to for local installs. Defaults to `/var/tmp`. Note: This variable is shared across
all roles in this collection to centralize depot staging and installation.

    integrity_vm_depot: ""

The name of the `.depot` file that will be copied to the target node for a local install. Make sure to place it
in the `files/` directory adjacent to your playbook.

    integrity_vm_vswitch_name: "vsw0"

The name of the default vswitch that vPars/VMs will use. Defaults to `vsw0`.

    integrity_vm_vswitch_lan: "0"

The interface index to bind the vswitch to (e.g. lan1). Defaults to `0` for lan0.

    integrity_vm_guests: []

The list of VMs to be created. Supports the following parameters:

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
        - iambryant.hpux.integrity_vm

## License

MIT

