Ansible Role Rust
=========

[![Molecule Test](https://github.com/diademiemi/ansible_role_rust/actions/workflows/molecule.yml/badge.svg)](https://github.com/diademiemi/ansible_role_rust/actions/workflows/molecule.yml)

This is an Ansible role to install and configure Rust.

This role can install Rust using system packages or rustup.

When running on an unsupported platform, rustup is used, no guarantees are made that this will work.

Requirements
------------
These platforms are supported:
- Ubuntu 20.04
- Ubuntu 22.04
- Debian 11
- Debian 12
- EL 8 (Tested on Rocky Linux 8)
- EL 9 (Tested on Rocky Linux 9)
- Fedora 40
- openSUSE Leap 15.5

<!--
- List hardware requirements here  
-->

Role Variables
--------------

Variable | Default | Description
--- | --- | ---
`rust_use_rustup` | `true` | Whether to use rustup to install Rust\
`rust_rustup_ensure_wget` | `true` | Whether to try to install wget if it is not installed. Requires a become password.
`rust_rustup_toolchains` | `["stable"]` | List of rustup toolchains to install
`rust_rustup_default_toolchain` | `{{ rust_rustup_toolchains[0] }}` | The default rustup toolchain
`rust_rustup_update` | `false` | Whether to update toolchains after installation
`rust_rustup_user` | `{{ ansible_user_id }}` | The user to install rustup for
<!--
`variable` | `default` | Variable example
`long_variable` | See [defaults/main.yml](./defaults/main.yml) | Variable referring to defaults
`distro_specific_variable` | See [vars/debian.yml](./vars/debian.yml) | Variable referring to distro-specific variables
-->

Dependencies
------------
<!-- List dependencies on other roles or criteria -->
None

Example Playbook
----------------

```yaml
    - role: "diademiemi.rust"
      tags: ['diademiemi', 'rust', 'setup']    ```

```

License
-------

MIT

Author Information
------------------

- diademiemi (@diademiemi)

Role Testing
------------

This repository comes with Molecule that run in Podman on the supported platforms.
Install Molecule by running

```bash
pip3 install -r requirements.txt
```

Run the tests with

```bash
molecule test
```

These tests are automatically ran by GitHub Actions on push. If the tests are successful, the role is automatically published to Ansible Galaxy.
