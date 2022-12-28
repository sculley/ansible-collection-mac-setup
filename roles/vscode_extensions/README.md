ansible-vscode-extensions-role
=========

An Ansible role to install Visual Code Studio extensions

![CI](https://github.com/sculley/ansible-collection-mac-setup/actions/workflows/ci.yml/badge.svg)
![Build](https://github.com/sculley/ansible-collection-mac-setup/actions/workflows/release.yml/badge.svg)


Requirements
------------

* Visual Code Studio - The application needs to be installed, if its not then the role will skip all the tasks 

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

| Variable                | Required | Default | Choices                   | Comments                                   |
|-------------------------|----------|---------|---------------------------|--------------------------------------------|
| vscode_extensions       | yes      | []      | list(string)              | Enter list of VSCode Extensions to install |

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - role: sculley.mac_setup.vscode_extensions

      vars:
        vscode_extensions:
          - DavidAnson.vscode-markdownlint

License
-------

See license.md

Author Information
------------------

[https://www.samculley.co.uk](https://samculley.co.uk)