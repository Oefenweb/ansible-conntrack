## conntrack

[![Build Status](https://travis-ci.org/Oefenweb/ansible-conntrack.svg?branch=master)](https://travis-ci.org/Oefenweb/ansible-conntrack) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-conntrack-blue.svg)](https://galaxy.ansible.com/Oefenweb/conntrack)

Manage `(nf_)conntrack` in Debian-like systems.

#### Requirements

None

#### Variables

* `conntrack_kernel_modules`: [default: `[]`]: List of kernel modules to load
* `conntrack_kernel_modules.{n}.name`: [required]: Name of the kernel module (e.g. `nf_conntrack`)
* `conntrack_kernel_modules.{n}.params`: [optional, default: `[]`]: List of parameters for this kernel module
* `conntrack_kernel_modules.{n}.params.{n}.name`: [required]: Name of the parameter
* `conntrack_kernel_modules.{n}.params.{n}.value`: [required]: Value of the parameter

* `conntrack_sysctl_settings`: [default: `[]`]: List of `sysctl` settings
* `conntrack_sysctl_settings.{n}.name`: [required]: Name of the `sysctl` setting
* `conntrack_sysctl_settings.{n}.value`: [required]: Value of the `sysctl` setting

## Dependencies

None

#### Example

```yaml
---
- hosts: all
  roles:
    - conntrack
  vars:
    conntrack_kernel_modules:
      - name: nf_conntrack
        params:
          - name: hashsize
            value: 16384
    conntrack_sysctl_settings:
      - name: net.netfilter.nf_conntrack_max 
        value: 65536
```

#### License

MIT

#### Author Information

* Mark van Driel
* Mischa ter Smitten

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Oefenweb/ansible-conntrack/issues)!
