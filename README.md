# Bootstrap

This repository contains all dot files used to tweak tools on Unix.

# How-to

When moving into a new host (bacteria style 🦠), install [mr](https://myrepos.branchable.com/) and [vcsh](https://github.com/RichiH/vcsh/blob/main/doc/INSTALL.md).

### Bootstrap repos config

```sh
cd ~ && csh clone git://github.com/Emilien-Foissotte/vcsh_mr_template.git mr
```

### Choose repositories

For instance, to activate `tmux-mac` configuration

```sh
cd ~/.config/mr/available.d/
ls -la
cd ../config.d/
ln -s  ../available.d/tmux-mac
```

### Update repositories

```sh
cd ~ && mr update
```

And that's it 🚀
