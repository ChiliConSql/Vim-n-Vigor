# Vim Environment Setup

based on [Vimcasts Episode #27](http://vimcasts.org/episodes/synchronizing-plugins-with-git-submodules-and-pathogen/) and [Pathogen](https://github.com/tpope/vim-pathogen#pathogenvim)

## Reconstruct From Git Repo

- clone the repo
```
# create the vim directory
mkdir ~/.vim
git clone https://github.com/ChiliConSQL/dotvim.git ~/.vim
```

- switch to the  directory, and fetch submodules:
```
cd ~/.vim
git submodule init
git submodule update
```

- to update a plugin
```
cd ~/.vim/bundle/plugin
git pull origin master
```

- to update all plugins, run this as a bash script
```
git submodule foreach git pull origin master
```

## Build It From Scratch

- create the folder and repo
```
mkdir -p ~/.vim/{bundle,autoload}
cd ~/.vim
```

- initialize the repo
```
git init
```

- download/copy pathogen.vim into autoload
```
curl -LSso autoload/pathogen.vim https://tpo.pe/pathogen.vim
git add autoload
git commit -m 'Initialize vim repo with Pathogen'
```

- add plugins

```
# let's start with sensible
git submodule add https://github.com/tpope/vim-sensible.git	bundle/sensible
```

- some goodies:

```
# surround text blocks with characters
git submodule add https://github.com/tpope/vim-surround.git bundle/surround

# comment out chunks of code
git submodule add https://github.com/tomtom/tcomment_vim.git bundle/tcomment

# navigate the directory with vinegar
git submodule add https://github.com/tpope/vim-vinegar.git bundle/vinegar

# do git from vim!
git submodule add https://github.com/tpope/vim-fugitive.git bundle/fugitive

# standard editor configuration
git submodule add https://github.com/editorconfig/editorconfig-vim.git bundle/editorconfig
```

- work with tmux
```
git submodule add https://github.com/christoomey/vim-tmux-navigator.git bundle/tmux-navigator

# configure tmux with Tmux Plugin Manager
echo "set -g @plugin 'christoomey/vim-tmux-navigator'" >> ~/.tmux.conf
run '~/.tmux/plugins/tpm/tpm'
```

- interact with databases
```
# the new plugin from The Pope
git submodule add https://github.com/tpope/vim-dadbod bundle/dadbod

# add .pgpass to use vim sql capabilities
echo 'localhost:5432:amadeus:imad:password' > ~/.pgpass
chmod 600 ~/.pgpass
```

- preview markdown
```
sudo pacman -S xdg-utils
npm -g install instant-markdown-d
git submodule add https://github.com/suan/vim-instant-markdown bundle/instant-markdown
```

- the Big Daddy of all plugins:
[You Complete Me][10] and its [github repo] [11]

- colors

```
git submodule add https://github.com/altercation/vim-colors-solarized bundle/colors-solarized
git submodule add https://github.com/jonathanfilip/vim-lucius.git bundle/colors-lucius
git submodule add https://github.com/Lokaltog/vim-distinguished bundle/colors-distinguished
git submodule add git://github.com/tomasr/molokai.git bundle/colors-molokai
git submodule add git://github.com/therubymug/vim-pyte.git bundle/colors-pyte
git submodule add https://github.com/jnurmine/Zenburn.git bundle/colors-zenburn
git submodule add https://github.com/cschlueter/vim-wombat.git bundle/colors-wombat
git submodule add https://github.com/dsolstad/vim-wombat256i.git bundle/colors-wombat256i
git submodule add https://github.com/nanotech/jellybeans.vim bundle/colors-jellybeans
```

- syntax
TODO
