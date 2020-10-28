# Prerequisites
Ansible must be installed on the host machine. See the official documentation on how to install it: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

## Community General Collection
Some roles (e.g. `flatpak`) depends on modules that are not part of Ansible core.

Those modules can be installed via `requirements.yml`:

`ansible-galaxy collection install -r requirements.yml`

# Configuration
Pre-defined variables can be used to configure each role. They can be found in the `${role}/vars/main.yml` file.
## flatpak
The following variables are available:
* `apps` - **required** - A dictionary where the key is the application name and the value is the flatpak name for this application.

## intellij
The following variables are available:
* `version` - **required** - the version of Intellij IDEA to be downloaded and installed. For example, `2020.2.3`.
* `checksum` - **required** - the sha256 checksum for the archive, which can be found on the Intellij IDEA download page.

# Run

To run all tasks in the playbook:
`ansible-playbook -i local.yml setup.yml -K`

The `-K` flag is used to ask for credentials for tasks that need elevated privileges.

The following tags are available:

* `library` - Install commonly used DNF libraries for development
* `flatpak` - Install commonly used applications using flatpak
* `intellij` - Install Intellij IDEA Ultimate

Tags can included/excluded using one of the methods described in https://docs.ansible.com/ansible/latest/user_guide/playbooks_tags.html

By default, all tasks will be executed.

# Debug

*Todo*
