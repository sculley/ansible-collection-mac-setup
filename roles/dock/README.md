# Ansible Role: macOS Dock Automation

This role automates the use of `dockutil` to manage the items in your macOS Dock. You can add, remove, and arrange Dock items.

## Requirements

  - **Homebrew**: Requires `homebrew` already installed (you can use `sculley.mac.homebrew` to install it on your Mac).

## Role Variables

Available variables are listed below, along with example values (see `defaults/main.yml`):

```yaml
dockitems_remove: []
```

Dock items to remove.

```yaml
dockitems_persist: []
```

Dock items to add. `pos` parameter is optional and will place the Dock item in a particular position in the Dock.

## Dependencies

  - (Soft dependency) `sculley.homebrew`

## Example Playbook

```yaml
    - hosts: localhost

      vars:
        dockitems_remove:
          - Launchpad
          - TV
          - Podcasts
          - 'App Store'

        dockitems_persist:
          - name: Messages
            path: "/Applications/Messages.app/"
          - name: Safari
            path: "/Applications/Safari.app/"
            pos: 2
          - name: Sublime Text
            path: "/Applications/Sublime Text.app/"
            pos: 3

      roles:
        - sculley.mac.homebrew
        - sculley.mac.dock
```

See the [Mac Setup Playbook](https://github.com/sculley/ansible-mac-setup-playbook) for an example of this role's usage.

## License

MIT / BSD

## Author Information

[Sam Culley](https://www.samculley.com/)
