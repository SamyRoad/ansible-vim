# Vim

  This is a non opinionated vim config: just install vim and a set of common bundles/plugins. All config, key bindings
  and magical stuff are left to your customizations.
  
  This role it is compatible with Debian/Ubuntu.
  
  We provide a cascade of config files to allow you to set your custom settings and install your desired plugins without
  hassle. Check our use cases.


## Use case #1: install for shared usage
  
  You want to install a custom vim settings and plugins in your remote server. This config is shared between all server
  users, but customized settings for a single user is allowed if you want.

  Set `vim_env` variable to `system` in your playbook.

  The common config is placed in `/etc/vim/vimrc.local` (for settings) and `/etc/vim/vimrc.bundles` (for plugins).

  If you need to overwrite any setting or install new plugins for a selected user, you need to put your settings in 
  these files: `~/.vimrc.local` and `~/.vimrc.bundles.local`

  **Important**: by default, plugins are installed for `root` user. In all other users you have to install plugins
  manually with command `vim +PluginInstall`.

  Refer to [Vundle documentation](https://github.com/VundleVim/Vundle.vim) for plugin management.


## Use case #2: install for a single user

  You want to use this ansible role to provision your own laptop and just want a customized vim for your user. All your
  config lives in your `$HOME` path, just like regular vim install.

  Set `vim_env` variable to `user` in your playbook and set `vim_users` variable with a list of users to install vim.

  The common config is placed in `~/vimrc` (for settings) and `~/vimrc.bundles` (for plugins).

  If you need to overwrite any setting or install new plugins for a selected user, you need to put your settings in 
  these files: `~/.vimrc.local` and `~/.vimrc.bundles.local`

  Refer to [Vundle documentation](https://github.com/VundleVim/Vundle.vim) for plugin management.


## Requirements

  Ansible  1.9 or greater

## Role Variables

  | Name                 | Description |
  | ----                 | ----------- |
  | `vim_env`            | Where to install vim: system or user.<br/> If you install it system-wide, all users will use your default configuration. |
  | `vim_users`          | List of users to install vim. Use it in conjunction with `vim_env`. |
  | `vim_plugins`        | List of vim plugins to install. Use [Vundle](https://github.com/gmarik/Vundle.vim) format. |
  | `vim_vundle_version` | Vundle version to install. |

## Dependencies

  None.

## License

  MIT

## Author Information

  Moisés Maciá <mmacia@gmail.com>
