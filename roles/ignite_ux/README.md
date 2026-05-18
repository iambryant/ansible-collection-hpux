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
in the `files/` directory adjacent to your playbook.

    logical_volumes:
      - lv_path: "/dev/vg00/lvol6"
        mount_path: "/opt"
        lv_size: 8192
      - lv_path: "/dev/vg00/lvol8"
        mount_path: "/var"
        lv_size: 16384

The list of logical volumes that you want to resize for Ignite-UX. Defaults to the values defined in HP's documentation
(see top of README).

ignite_user_files: []

The list of files you want to be copied to the Ignite-UX server. Supports the following parameters:

| Parameter      | Type    | Required | Description                                 |
| :---           | :---    | :---     | :---                                        |
| `src`          | String  | **Yes**  | The file to copy to the target node.        |
| `dest`         | String  | **Yes**  | The destination directory to place the file.|

Make sure to place the files inside the `files/` directory adjacent to your playbook.

ignite_user_templates: []

The list of templates you want to be rendered on the Ignite-UX server. Supports the following parameters:

| Parameter      | Type    | Required | Description                                      |
| :---           | :---    | :---     | :---                                             |
| `src`          | String  | **Yes**  | The template to render on the target node.       |
| `dest`         | String  | **Yes**  | The destination directory to place the template. |

Make sure to place the templates inside the `templates/` directory adjacent to your playbook.

## Dependencies

None.

## Example Playbook

    - hosts: all
      become: true
      vars:
        ansible_python_interpreter: /usr/local/bin/python3
      roles:
        - lpars.hpux.ignite_ux

## License

MIT
