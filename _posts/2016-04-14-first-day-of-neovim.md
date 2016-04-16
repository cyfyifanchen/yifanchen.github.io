---
title: "First Day of Neovim"
layout: post
date: 2016-04-14 
tag:
- vim 
- neovim
blog: true
star: false
---

## First day of using Neovim

As my [`.vimrc`](https://github.com/yifanchen/dotfiles/blob/master/.vimrc) gets complicated, Vim can get slow often, I had to take off some great features to maintain the sweet speed. I started to use code style checkers and linters recently, fond out Vim gets even slower when opening big `.js` files with code style checkers on. That's probably the biggest problem the current version of Vim has, it doesn't work asynchronously. In another word, Vim freezes when the former action being
executed. However, the next version of Vim, 8.0, has asynchronous processing according to it's pre-release [doc](https://github.com/vim/vim/blob/master/runtime/doc/version8.txt). This is the best thing can ever happen to Vim, but I am getting very impatient. I decided to try Neovim out.

Neovim is very new, in fact the very first beta version is still not released. But, I've heard good things from other Vimmers, especially how faster it is comparing with Vim. Vim's speed doesn't bother me much before, but it has started lately as my plugin collection gets heavy. Neovim has the asynchronous process, not much plugins have the capabilities can take advantages of it. I believe in the future more and more plugins will be built that way.

After few hours installing and googline. Amazingly, all the plugins, themes, colors, settings work already in Neovim. How awesome is that? Believe me, configing Vim isn't fun at all. But, Neovim has it's game down to make the [transition](https://neovim.io/doc/user/nvim_from_vim.html) quite friendly to Vimmers. In order to get full benefits from Neovim, couple plugins I definitely need to swap. First, Neomake to Syntastic. Second, Vim-Plug to Bundle. As I said, this two plugins are both built-in with asynchronous processing. Can't wait to try the result.
