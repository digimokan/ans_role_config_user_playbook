# ans_role_config_user_playbook

Clone playbook used to set up the machine, and emplace vault password.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_user_playbook.svg?label=release)](https://github.com/digimokan/ans_role_config_user_playbook/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* Clone a machine-setup playbook to user directory.
* Copy vault password file from root, and optionally symlink it.

## Supported Operating Systems

* Ubuntu
* Arch Linux
* FreeBSD

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_user_playbook
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Clone playbook used to set up the machine, and emplace vault password"
         ansible.builtin.include_role:
           name: ans_role_config_user_playbook
           public: true
         vars:
           cfg_user_playbook_pb_name: 'ans_plbk_fedora_mate_user7'
           cfg_user_playbook_target_user_name: 'admin5'
           cfg_user_playbook_target_pb_clone_dir: '/home/admin5'
           cfg_user_playbook_target_vault_passwd_symlink_to_path: '/home/user7/admin_vault_password.txt'
   ```

## Role Options

Vars with default values, which can be overridden in the playbook:

  * [overridable](../defaults/main/overridable/main.yml)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_user_playbook/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).

