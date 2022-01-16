# Ansible Role: Kitty terminal emulator

An Ansible Role that installs [Kitty](https://sw.kovidgoyal.net/kitty/) on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    # If no version is specified, the latest version will be installed.
    kitty_version: 0.24.1

    # If no installation prefix is specified, /usr/local is used.
    kitty_install_prefix: $HOME/.local

    # List of user environment files to add conditional export to the system PATH of a directory with app binary.
    # Only existing files with write access for the current ansible_user will be processed.
    # If not specified, empty list is used.
    awscli_env_files_to_modify:
      - $HOME/.profile
      - $HOME/.bashrc
      - $HOME/.zshenv

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - ansible-role-kitty
```

## License

MIT
