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

As my [`.vimrc`](https://github.com/yifanchen/dotfiles/blob/master/.vimrc) gets complicated, Vim can get slow often(mainly because some poorly written plugins), I had to take off some great features to maintain its sweet speed. I started using code style checkers and linters recently, I found out Vim gets even slower when opening big `.js` files with code style checkers on. That's probably the biggest problem the current version of Vim has, it doesn't work asynchronously. In another word, Vim freezes when the former action is being
executed. However, the next version of Vim, 8.0, has asynchronous processing according to it's pre-release [doc](https://github.com/vim/vim/blob/master/runtime/doc/version8.txt). This is the best thing that can happen to Vim, but I am getting very impatient. I decided to try Neovim out.

Neovim is very new, in fact the very first beta version is still not released. But, I've heard good things from other Vimmers, especially how fast it is comparing with Vim. Vim's speed doesn't bother me much before, but it has started lately as my plugin collection gets heavy. Neovim has the asynchronous process, not much plugins have the capabilities can take advantages of it. I believe in the future more and more plugins will be built that way.

After few hours configing and googling. Amazingly, all the plugins, themes, colors, settings work already in Neovim. Configing Vim isn't fun, surprisingly Neovim has it's game down to make the [transition](https://neovim.io/doc/user/nvim_from_vim.html) quite friendly to Vimmers. There are couple things I found quite awesome that comes in with Neovim already, built-in Terminal and better mouse integration. I use Tmux for my session management, so the built-in Terminal won't be usefull much to me for now. But, I like the idea of having it, maybe in the future, I don't have to use Tmux anymore. The mouse integration is solid, it doesn't feel buggy at all. I am a huge believer of mouse-free wrokflow, so I might disable mouse in Neovim at some point. However, it's good to know that Neovim comes with better mouse integration. In order to get full benefits from Neovim, the following plugins I will need to install or switch.

    Vim-Plug
    fzf
    fzf-vim
    Neocomplete
    Neosnippet
    Neomake

These plugins all support async processing. Can't wait to ry the result.

Well, I am very happy with it. Last step:

    alias vi="nvim"

