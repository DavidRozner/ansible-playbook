# Ansible Playbook

This Ansible playbook automates the setup of a freshly installed operating system to make it development-ready. 🚀

## Installation

Clone the repository using a Personal Access Token (PAT):
```bash
git clone https://<username>:<PAT>@github.com/DavidRozner/ansible-playbook.git
```

Alternatively, download the repository manually as a ZIP file and extract it.

## Running the Script

1. Navigate to the playbook directory:
   ```bash
   cd ansible-playbook
   ```
2. Run the playbook:
   ```bash
   ansible-playbook setup.yml
   ```

## Prerequisites

Before running the playbook, ensure you have the following:
- Your computer's sudo password
- The Ansible vault password (used to decrypt SSH keys)

## Roles and Tasks

This playbook is organized into the following roles, each with specific tasks:

### System Role 
- Update `apt` packages
- Install essential tools and libraries:
  - `git`, `stow`, `zsh`, `tmux`, `xclip`, `eza`, `unzip`
  - `curl`, `bat`, `gcc`, `clang`, `build-essential`, `libstdc++-12-dev`
  - `wget`, `fzf`

### Zsh Role
- Install and configure Oh My Zsh:
  - Removes any previous installations, including `.zshrc`
  - Installs and updates Zinit for plugin management
  - Sets Zsh as the default shell

### Neovim Role
- Install and configure Neovim (Nvim)

### Tmux Role
- Install Tmux Plugin manager

### SSH Role
- Copy public SSH keys to the user's `.ssh` directory
- Decrypt private SSH keys and store them securely in the `.ssh` directory

### Dotfiles Role
- Clone and configure dotfiles for tools like NVChad, Zsh, Tmux, and Git
- Use GNU Stow to symlink dotfiles, ensuring consistent configuration across systems

### Fonts Role
- Download and install the Hack Nerd Font
- Set it as the default terminal font

### LSP Role
- Install Language Server Protocol (LSP) support for Neovim
  - Includes pre-configured support for:
    - TypeScript
    - Rust
    - Go
    - Java
    - C#
    - C++
    - Python
    - PHP
  - Uncomment additional LSPs in `roles/lsp/tasks/main.yml` as needed

  ## Post Install
  Plugins are not installed by default, by they should install after first launch of tmux, zsh, and Nvim

  Sometimes is also necessary to logout for zsh to be a default Shell
