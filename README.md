# Ansible MacOS Playbook

This is the playbook I use after a clean install of MacOS to set everything up.

## Roles/Tasks

- Installs Homebrew packages and app casks (Role `homebrew`)
- Installs App Store apps with [`mas-cli`](https://github.com/mas-cli/mas) (Role `mas`)
- Modifies MacOS settings (Role `settings`)
- TODO: setup VSCode
- TODO: customize terminal

## Installation

1. Install [Homebrew](https://brew.sh).
2. Install Ansible (`brew install ansible`)
3. Copy `default.config.yml` to `config.yml` and edit the configuration to your likings.
   - **Don't skip this, otherwise your computer will be provisioned like mine :)**
4. Run `ansible-playbook main.yml`. Enter your account password when prompted.
   - If you have a configuration stored elsewhere (e.g. in a dotfiles folders), run `ansible-playbook main.yml --extra-vars=@/path/to/my/config.yml`
   - `mas-cli` is installed by `homebrew` Role. If you want to customize and run only selected roles, please take care that required tools are present.

## Updating a fork with the latest changes from this repository

If you forked this repository and want to include its latest changes without losing your own,
add this repository as an upstream and rebase it onto your fork:

```bash
git remote add upstream git@github.com:jeromegamez/ansible-macos-playbook.git
git fetch upstream
git rebase upstream/master
```

## Acknowledgements

This playbook is heavily inspired by
[Jeff Geerling's mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook).

The macOS settings (a.k.a. `defaults write`s) are mostly taken from
[Mathias Bynens' defaults scripts](https://mths.be/macos) or from one of the
dotfiles repos from [http://dotfiles.github.io](http://dotfiles.github.io).
