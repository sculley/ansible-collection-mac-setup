# Mac Setup Collection for Ansible

[![MIT licensed][badge-license]][link-license]
[![Galaxy Collection][badge-collection]][link-galaxy]
[![CI][badge-gh-actions]][link-gh-actions]

Roles included in this collection (click on the link to see the role's README and documentation):

  - `sculley.mac_setup.iterm2` ([documentation](https://github.com/sculley/ansible-collection-mac-setup/blob/master/roles/iterm2/README.md))
  - `sculley.mac_setup.ohmyzsh` ([documentation](https://github.com/sculley/ansible-collection-mac-setup/blob/master/roles/ohmyzsh/README.md))
  - `sculley.mac_setup.powerlevel10k` ([documentation](https://github.com/sculley/ansible-collection-mac-setup/blob/master/roles/powerlevel10k/README.md))
  - `sculley.mac_setup.vscode` ([documentation](https://github.com/sculley/ansible-collection-mac-setup/blob/master/roles/vscode/README.md))

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
    iterm2_font_urls:
      - https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf
    iterm2_dynamic_profile_urls:
      - https://raw.githubusercontent.com/sculley/iterm2-setup/main/MacOS-iTerm2.json
    iterm2_shell_integration: true
    iterm2_set_dynamic_default_profile_script_url: "https://raw.githubusercontent.com/sculley/iterm2-setup/main/set-dynamic-default-profile.py"
    iterm2_set_dynamic_default_profile_script_name: "set-dynamic-default-profile.py"

  roles:
    - sculley.mac.iterm2
```

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
