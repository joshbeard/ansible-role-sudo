# Ansible Role for Sudo

Deliberately simple Ansible role for managing _sudo_.

## Installation

Example `requirements.yml` file for `ansible-galaxy`:

```yaml
roles:
  - src: https://github.com/joshbeard/ansible-role-sudo.git
    scm: git
    version: '0.1.0'
    name: jbeard.sudo
```

## Usage

### Variables

| Variable              | Description
| --------------------- | --------------------------------------------------------- |
| `sudoers_dir`         | Absolute path to the `sudoers.d` directory.
| `sudoers_files`       | A _Dict_ of sudoers files to create. The _key_ is the filename and a `content` key (string) is the contents of the file.
| `lookup_default_vars` | Toggles looking up the OS-specific defaults from the 'vars/' directory. This requires facts to be available. It can be disabled if `sudoers_dir` is explicitly set.

Refer to [`defaults/main.yml`](defaults/main.yml) and [`vars/`](vars/).

### Example Configuration

```yaml
# Absolute path to sudoers.d directory
sudoers_dir: /usr/local/etc/sudoers.d

# Dictionary of sudoers files to create.
sudoers_files:
  # This will create /usr/local/etc/sudoers.d/wheel
  wheel:
    content: |
      %wheel ALL=(ALL) NOPASSWD: ALL
      # This is a test
```
