# ansible-role-bashrc

Ansible role that stows the `bashrc` package from the personal dotfiles repository and makes `~/.bashrc` source `~/.my_bashrc`.

## Requirements

- Debian or Ubuntu host
- `become: true` privileges (sudo)
- Depends on the `dotfiles` role, which clones the dotfiles repo to `dotfiles_path` and provides `dotfiles_path`, `user_home_path` defaults. `ansible_user` must be set.

## Example Playbook

```yaml
- hosts: all
  become: true
  roles:
    - role: bashrc
```

## Manual setup (without Ansible)

```
sudo apt install stow git
git clone https://github.com/Varssos/dotfiles.git ~/dotfiles
cd ~/dotfiles && stow -R bashrc
echo 'source ~/.my_bashrc' >> ~/.bashrc
```
