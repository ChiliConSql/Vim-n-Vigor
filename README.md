[1]: https://github.com/tpope/vim-sensible.git
[2]: https://github.com/tpope/vim-vinegar.git
[3]: https://github.com/tpope/vim-surround.git
[4]: https://github.com/tpope/vim-unimpaired.git
[5]: git://github.com/ervandew/supertab.git
[6]: https://github.com/christoomey/vim-tmux-navigator.git
[7]: git://github.com/jpalardy/vim-slime.git

[10]: https://github.com/editorconfig/editorconfig-vim.git
[11]: https://github.com/tomtom/tcomment_vim.git
[12]: https://github.com/tpope/vim-fugitive.git
[13]: git://github.com/sirver/ultisnips.git
[14]: https://github.com/honza/vim-snippets.git
[15]: http://valloric.github.io/YouCompleteMe/
[16]: https://github.com/Valloric/YouCompleteMe

[20]: https://github.com/tpope/vim-dadbod
[21]: https://github.com/suan/vim-instant-markdown

[22]: https://github.com/alfredodeza/pytest.vim.git

[29]: https://github.com/Glench/Vim-Jinja2-Syntax.git
[NOT DONE YET]: # (
[23]: git://github.com/exu/pgsql.vim.git
[24]: https://github.com/othree/html5.vim.git
[25]: https://github.com/posva/vim-vue.git
[26]: https://github.com/hail2u/vim-css3-syntax.git
[27]: https://github.com/pangloss/vim-javascript.git
[28]: https://github.com/elzr/vim-json
)
[30]: https://github.com/davidhalter/jedi-vim.git

[40]: https://github.com/altercation/vim-colors-solarized
[41]: https://github.com/jonathanfilip/vim-lucius.git
[42]: https://github.com/Lokaltog/vim-distinguished
[43]: git://github.com/tomasr/molokai.git
[44]: git://github.com/therubymug/vim-pyte.git
[45]: https://github.com/jnurmine/Zenburn.git
[46]: https://github.com/cschlueter/vim-wombat.git
[47]: https://github.com/dsolstad/vim-wombat256i.git
[48]: https://github.com/nanotech/jellybeans.vim

[100]: https://github.com/rking/ag.vim.git
[101]: git://github.com/vim-scripts/bash-support.vim.git
[102]: https://github.com/ameade/qtpy-vim.git
[104]: git://github.com/fs111/pydoc.vim.git

[//]: # (These need to be investigated)
[00]: https://github.com/michaeljsmith/vim-indent-object
[00]: https://github.com/ivalkeen/vim-simpledb
[00]: https://github.com/vim-scripts/scratch.vim.git
[00]: https://github.com/tommcdo/vim-exchange.git
[00]: https://github.com/bling/vim-airline
[00]: https://github.com/tpope/vim-repeat.git
[00]: git://github.com/fholgado/minibufexpl.vim.git
[00]: https://github.com/godlygeek/tabular.git
[00]: https://github.com/sjl/gundo.vim.git
[00]: https://github.com/tpope/vim-abolish.git
[00]: https://github.com/nelstrom/vim-markdown-folding.git
[00]: https://github.com/rstacruz/sparkup.git
[00]: https://github.com/Lokaltog/vim-easymotion.git

[000]: https://github.com/kien/ctrlp.vim.git
[000]: git://github.com/vim-scripts/taglist.vim.git

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

### Set Up

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

### Add Plugins

- let's start with sensible and vinegar to navigate dirs
```
git submodule add https://github.com/tpope/vim-sensible.git	bundle/sensible
git submodule add https://github.com/tpope/vim-vinegar.git bundle/vinegar
```

- some essentials
```
# surround text blocks with characters
git submodule add https://github.com/tpope/vim-surround.git bundle/surround
# tab completion
git submodule add git://github.com/ervandew/supertab.git bundle/supertab
# easy movement
git submodule add https://github.com/tpope/vim-unimpaired.git bundle/unimpaired
```

- coding functionality
```
# standard editor configuration
git submodule add https://github.com/editorconfig/editorconfig-vim.git bundle/editorconfig
# comment out chunks of code
git submodule add https://github.com/tomtom/tcomment_vim.git bundle/tcomment
# do git from vim!
git submodule add https://github.com/tpope/vim-fugitive.git bundle/fugitive
```

- work with tmux
```
git submodule add https://github.com/christoomey/vim-tmux-navigator.git bundle/tmux-navigator
# configure tmux with Tmux Plugin Manager
echo "set -g @plugin 'christoomey/vim-tmux-navigator'" >> ~/.tmux.conf
run '~/.tmux/plugins/tpm/tpm'
```

- slather on some slime
```
git submodule add git://github.com/jpalardy/vim-slime.git bundle/slime
```
   make it work with tmux by having the following in .vimrc
       let g:slime_target="tmux

- preview markdown
```
sudo pacman -S xdg-utils
npm -g install instant-markdown-d
git submodule add https://github.com/suan/vim-instant-markdown bundle/instant-markdown
```

- can't live without snippets
```
git submodule add git://github.com/sirver/ultisnips.git bundle/ultisnips
#default snippets for ultisnips
git submodule add https://github.com/honza/vim-snippets.git bundle/snippets
```

- the Big Daddy of all plugins

[You Complete Me][15] and its [github repo][16]

### Colors

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

### SQL

- interact with databases
```
# the new plugin from The Pope
git submodule add https://github.com/tpope/vim-dadbod bundle/dadbod
```

- connect to postgres
```
echo 'localhost:5432:amadeus:imad:password' > ~/.pgpass
chmod 600 ~/.pgpass
```

### Python

- [jinja syntax][29]
```
git submodule add https://github.com/Glench/Vim-Jinja2-Syntax.git bundle/syntax-jinja
```

### Syntax

TODO

## Plugin List

### Essential

- [Sensible][1] -
   basic vim defaults
- [Vinegar][2] -
   navigate directory tree
- [Surround][3] -
   easily put markers/quotes around text blocks
- [Unimpaired][4] -
   movement enhancements
- [Supertab][5] -
   tab completion plugin
- [Tmux-Navigator][6] -
   synchronize window movements with Tmux
- [Slime][7] -
   run commands in shell(**including** Tmux) from vim

### Coding
- [EditorConfig][10] -
   default editor settings
- [TComment][11] -
   comment out code blocks
- [Fugitive][12] -
   operate git from inside vim!
- [UltiSnips][13] -
   ultimate snippets!
- [Snippets][14] -
   snippets definitions for UltiSnips
- [You-Complete-Me][15] -
   awesome completion!

### Syntax
- [Dadbod][12] -
   database interface!
- [Instant-Markdown][13] -


### Python
**TODO**
- [PyTest][22] -
   run tests from vim
- [Jedi][30] -
    made obsolete by [You-Complete-Me][15]

### Colors
- [Solarized][40] -
    universal standard
- [Lucius][41] -
    even better than Solarized?
- [Distinguished][42] -
    what is it good for?
- [Molokai][43] -
    what is it good for?
- [Vim-Pyte][44] -
    what is it good for?
- [Zenburn][45] -
    what is it good for?
- [Wombat][46] -
    what is it good for?
- [Wombat256][47] -
    what is it good for?
- [JellyBeans][48] -
    what is it good for?

### Look Into
Only get plugins with solid stars
- [PyDoc][104] -
   investigate
- [AG][100] -
   stay with grep instead?
- [Bash-Support][101] -
   complicates things and does not do much besides snippets that we can add ourselves
- [QtPy][102] -
   using pytest instead

