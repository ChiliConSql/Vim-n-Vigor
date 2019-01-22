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
