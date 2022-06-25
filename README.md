# Mac Setup Collection for Ansible

[![MIT licensed][badge-license]][link-license]
[![Galaxy Collection][badge-collection]][link-galaxy]
[![CI][badge-gh-actions]][link-gh-actions]

This collection includes helpful Ansible roles and content to help with macOS automation. For a good example of the collection's usage, see the [Mac Setup Playbook](https://github.com/sculley/ansible-mac-setup-playbook).

Roles included in this collection (click on the link to see the role's README and documentation):

  - `sculley.mac_setup.homebrew` ([documentation](https://github.com/sculley/ansible-collection-mac-setup/blob/master/roles/homebrew/README.md))
  - `sculley.mac_setup.dock` ([documentation](https://github.com/sculley/ansible-collection-mac-setup/blob/master/roles/dock/README.md))

## Installation

Install via Ansible Galaxy:

```
ansible-galaxy collection install sculley.mac_setup
```

Or include this collection in your playbook's `requirements.yml` file:

```
---
collections:
  - name: sculley.mac
```

For a real-world example, see my [Mac Setup Playbook requirements file](https://github.com/sculley/ansible-mac-setup-playbook/blob/master/requirements.yml).

### Role Requirements

Requires separate installation of the `elliotweiser.osx-command-line-tools` role. Because Ansible collections are not able to depend on roles, you will need to make sure that role is installed either by manually installing it with the `ansible-galaxy` command, or adding it under the `roles` section of your `requirements.yml` file:

```yaml
---
roles:
  - name: elliotweiser.osx-command-line-tools

collections:
  - name: sculley.mac_setup
```

## Usage

Here's an example playbook which installs some Mac Apps (assuming you are signed into the App Store), CLI tools via Homebrew, and Cask Apps using Homebrew:

```yaml
- hosts: localhost
  connection: local
  gather_facts: false

  vars:
    mas_installed_app_ids:
      - 424389933 # Final Cut Pro
      - 497799835 # Xcode

    homebrew_installed_packages:
      - node
      - nvm
      - redis
      - ssh-copy-id
      - pv

    homebrew_cask_apps:
      - docker
      - firefox
      - google-chrome
      - vlc

  roles:
    - sculley.mac.homebrew
    - sculley.mac.mas
```

For a real-world usage example, see my [Mac Setup Playbook](https://github.com/sculley/ansible-mac-setup-playbook).

See the full documentation for each role in the role's README, linked above.

## License

MIT

## Author

[Sam Culley](https://www.samculley.com)

[badge-gh-actions]: https://github.com/sculley/ansible-collection-mac-setup/workflows/CI/badge.svg?event=push
[link-gh-actions]: https://github.com/sculley/ansible-collection-mac-setup/actions?query=workflow%3ACI
[badge-collection]: https://img.shields.io/badge/collection-sculley.mac__setup-blue
[link-galaxy]: https://galaxy.ansible.com/sculley/mac_setup
[badge-license]: https://img.shields.io/github/license/sculley/ansible-collection-mac-setup.svg
[link-license]: https://github.com/sculley/ansible-collection-mac-setup/blob/master/LICENSE
[badge-gh-actions]: https://github.com/sculley/ansible-collection-mac-setup/workflows/CI/badge.svg?event=push
