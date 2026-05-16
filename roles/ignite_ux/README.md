<img src="https://raw.githubusercontent.com/lpars/ansible-collection-hpux/main/roles/ignite_ux/images/successful-install.png" width="250" height="156" alt="Successful Install" />

# Ansible Role: Ignite-UX

This role installs Ignite-UX as per HP's [documentation](https://docs.google.com/viewer?url=https://community.hpe.com/hpeb/attachments/hpeb/itrc-156/498503/1/363239.pdf).

## Requirements

* **OS:** HP-UX 11i v3 (B.11.31) on Itanium (IA64).
* **Python:** Ansible requires Python 3. See the [HP-UX Porting and Archive Centre](http://hpux.connect.org.uk)
for compatible Python packages.

## Role Variables

    ignite_staging_dir: "/var/tmp"

The temporary directory to copy `.depot` files to for local installs.

    ignite_depot: ""

The name of the `.depot` file that will be copied to the target node for a local install. Make sure to place it
in the `files` directory of your playbook.

    logical_volumes:
      - lv_path: "/dev/vg00/lvol6"
        mount_path: "/opt"
        target_size: 8192
      - lv_path: "/dev/vg00/lvol8"
        mount_path: "/var"
        target_size: 16384

The list of logical volumes that you want to resize for Ignite-UX. Defaults to the values defined in HP's documentation
(see top of README).

## Dependencies

    - community.general

## Example Playbook

    - name: "Deploy Ignite-UX"
      hosts: ignite_ux
      become: true
      vars:
        ansible_python_interpreter: "/usr/local/bin/python3"
        ansible_remote_tmp: "/var/tmp/.ansible"
        ignite_depot: "HP_UX_11i_v3_Ignite-UX-11.31_C.7.29.2_HP-UX_B.11.11_32_64.depot"
        ignite_user_files:
          - src: "bootptab"
            dest: "/etc/bootptab"
          - src: "instl_boottab"
            dest: "/etc/opt/ignite/instl_boottab"
      roles:
        - lpars.hpux.ignite_ux

## License

MIT
