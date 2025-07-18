# Bootstrap

This repository contains all dot files used to tweak tools on Unix.

# How-to

When moving into a new host (bacteria style 🦠), install [mr](https://myrepos.branchable.com/) and [vcsh](https://github.com/RichiH/vcsh/blob/main/doc/INSTALL.md).

## Bootstrap repos config

```sh
cd ~ && vcsh clone git://github.com/Emilien-Foissotte/vcsh_mr_template.git mr
```

## Choose repositories

For instance, to activate `tmux-mac` configuration

```sh
cd ~/.config/mr/available.d/
ls -la
cd ../config.d/
ln -s  ../available.d/tmux-mac
```

## Update repositories

```sh
cd ~ && mr update
```

And that's it 🚀

# Personalize

## Create a new repository for a tool configuration

Initialize the vcsh repo

```sh
vcsh init my_new_repo
```

(Optional) Tweak the config

```sh
cd ~/.config/vcsh/repo.d/my_new_repo.git
git config --local user.email john.doe@domain.com
git config --local user.name "John DOE"
```

Add the config file for this repo

```sh
vcsh my_new_repo add .
vcsh my_new_repo commit -m "feat: init repository"
vcsh my_new_repo push
```

Make it available to `my`

Create a `.vcsh` file under `~/.config/mr/available.d/`

```sh
[$HOME/.config/vcsh/repo.d/my_new_repo.git]
checkout = vcsh clone git@github.com:John-Doe/my_new_repo.git my_new_repo update = vcsh my_new_repo pull
push     = vcsh my_new_repo push
status   = vcsh my_new_repo status
gc       = vcsh my_new_repo gc
```

_Be careful to update all my_new_repo entries with your vcsh repository name_

Add it to your global `mr` config :

```sh
vcsh mr add ~/.config/mr/available.d/my_new_repo.vcsh
vcsh mr commit -m "feat: add my_new_repo vcsh config"
vcsh mr push
```

Activate it on your local workstation :

```sh
cd ~/.config/mr/config.d
ln -s ../available.d/my_new_repo.vcsh
cd ~
mr update
```

Et voilà, `mr` take care of carrying on all the update you've made on other repository to keep a consistent config.
Play with a mix of available and activated vcsh repositories to mix along MacOS, Linux, Windows hosts !

(Optional) Pro-Gamer move :
_As vcsh tends to be very noisy, due to tracking to all of your ~ files, you can ignore by default all file and only track modification on specific already added files_

```sh
vcsh write-gitignore my_new_repo
```
