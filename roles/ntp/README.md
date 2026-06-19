# Ansible Role: NTP

This role configures NTP as per HP's [documentation](https://support.hpe.com/hpesc/public/docDisplay?docLocale=en_US&docId=sf000068260en_us).

## Requirements

* **Python:** Ansible requires Python, which HP-UX does not include by default. See the [HP-UX Porting and Archive Centre](http://hpux.connect.org.uk)
for compatible Python packages.

## Role Variables

    ntp_servers:
      - 0.pool.ntp.org
      - 1.pool.ntp.org

The list of NTP servers to use. Defaults to `0.pool.ntp.org` and `1.pool.ntp.org`.

## Dependencies

None.

## Example Playbook

    - hosts: all
      become: true
      vars:
        ansible_python_interpreter: /usr/local/bin/python3
      roles:
        - iambryant.hpux.ntp

## License

MIT

