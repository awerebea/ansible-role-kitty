# Ansible Role: Kitty terminal emulator

An Ansible Role that installs [Kitty](https://sw.kovidgoyal.net/kitty/) on Linux.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    # If no version is specified, the latest version will be installed.
    kitty_version: 0.24.1

    # If no installation prefix is specified, during installation, the kitty.app directory
    # with app binaries will be placed in the standard installation script location, ~/.local.
    kitty_install_dir: $HOME/.kitty

    # The path containing a symbolic link to the main Kitty program in the installation directory.
    # If not specified, the link and its containing directory will not be created.
    kitty_bin_dir: $HOME/.local/bin

    # The path containing a modified copy of standard kitty.desktop file from the installation directory.
    # If not specified, the copy of .desktop file and its containing directory will not be created.
    kitty_desktop_file_dir: $HOME/.local/share/applications

    # If the directory for downloading installation script and release tarball is not specified,
    # /tmp/kitty-installer-ansible is used.
    kitty_download_dir: $HOME/Downloads/kitty

    # List of user environment files to add conditional export to the system PATH of a directory with link to the app binary.
    # Only existing files with write access for the current ansible_user will be processed.
    # If not specified, empty list is used.
    kitty_env_files_to_modify:
      - $HOME/.profile
      - $HOME/.bashrc
      - $HOME/.zshenv

**NOTE:** By default, the base tasks of a role are skipped if the application is already installed in the desired
<br />installation directory and no version upgrade is required.
<br />&nbsp;&nbsp;&nbsp;&nbsp;If you want to create a symbolic link to the main Kitty program in the bin directory, or add a conditional export
<br />to the system PATH of a directory with a link to the app binary, and create the appropriate directories as needed,
<br />after the Playbook has already been run once, you can force the launch base role tasks by defining
<br />the `update_apps` variable and adding `kitty` to the list. For example:
``` bash
$ ansible-playbook main.yaml -e "update_apps=[kitty]"
```
This approach is also used to force an update to the latest available release.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: ansible-role-kitty
      kitty_bin_dir: $HOME/.local/bin
      kitty_desktop_file_dir: $HOME/.local/share/applications
```

## License

MIT
