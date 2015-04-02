Vim
=========

Install and configure Vim for terminal usage.

Compatible with Debian/Ubuntu and Mac OSX.

Once installed, you need to run manually `vim +PluginInstall +qall` in order to install all plugins.

If you need to overwrite any setting or install new plugins, use these files: `~/.vimrc.local` and
`~/.vimrc.bundles.local`

Requirements
------------

None.

Role Variables
--------------

| Name          | Description |
| ----          | ----------- |
| `vim_env`     | Where to install vim: system or user.<br/> If you install it system-wide, all users will use your default configuration. |
| `vim_users`   | List of users to install vim. Use it in conjunction with `vim_env`. |
| `vim_plugins` | List of vim plugins to install. Use [Vundle](https://github.com/gmarik/Vundle.vim) format. |

Dependencies
------------

None.

License
-------

MIT

Author Information
------------------

Moisés Maciá <mmacia@gmail.com>
