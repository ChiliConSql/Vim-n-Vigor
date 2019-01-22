#My .vim configuration
based on [Vimcasts Episode #27](http://vimcasts.org/episodes/synchronizing-plugins-with-git-submodules-and-pathogen/) and [Pathogen](https://github.com/tpope/vim-pathogen#pathogenvim)

## From Scratch

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
git add autoload
git commit -m 'Initialize vim repo with Pathogen'
```

- add plugins
let's start with sensible
```
git submodule add https://github.com/tpope/vim-sensible.git	bundle/sensible
```

some goodies:
- surround text blocks with characters
- comment out chunks of code
- navigate the directory with vinegar
- do git from vim!
```
git submodule add https://github.com/tpope/vim-surround.git bundle/surround
git submodule add https://github.com/tomtom/tcomment_vim.git bundle/tcomment
git submodule add https://github.com/tpope/vim-vinegar.git bundle/vinegar
git submodule add https://github.com/tpope/vim-fugitive.git bundle/fugitive
```

## From git repo:

- clone the repo
```sh
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

