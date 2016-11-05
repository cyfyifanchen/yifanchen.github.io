---
title: "How to Set Color Scheme in Neovim"
layout: post
date: 2016-10-31
tag:
- Neovim
- vim
- color scheme
blog: true
star: false
---

Making a color scheme looks the way it should be in Vim is notoriously cumbersome. Cut to the chase. I am going to share some tips with you on how to set the color scheme correct in Vim and Tmux.

First of all, use [Neovim](https://neovim.io/) instead of Vim. Why? Neovim offers a much better support of True Color. If you want to stick with traditional Vim and invest your time on figuring out how True Color works, read [this](https://deductivelabs.com/en/2016/03/using-true-color-vim-tmux/). If not, I strongly recommend you using Neovim not only because it is going to enlighten the speed quite a bit, but also because you are dealing with a more modern code base that maintained by a bunch of Vim enthusiasts. That means whenever you run into a problem and open an issue on their [Github Page](https://github.com/neovim/neovim), the solution will likely be there right away. I have been using Neovim for more than half year, and I have been entirely happy with it. I have written a [blog]({{site.url}}/first-day-of-neovim) on how to make the transition if you feel like you want to read it.

Next, let's go get a good [color scheme](http://vimcolor.com). Pick the color you like. I recommend dark themes(I am going to use Vim-One as an example). Now, we want to call the color scheme via Neovim plugin managers. I recommend [Vim Plug](https://github.com/junegunn/vim-plug). After this, you need the following lines in your `.vimrc`.

<script src="https://gist.github.com/yifanchen/8f1068714aaef59c151df5011e5fc136.js"></script>

Now, source your `.vimrc`. You should be able to see the changes immediately. If it doesn't work, probably means your Neovim is outdated. Run the following command to get the latest update of Neovim.

    brew upgrade neovim

If it still doesn't work(most likely not happening when you are up-to-date on everything), run the following lines to force the color change in your terminal emulator(I use iTerm2). The following commands check the version of your Neovim and set the condition to toggle when your version not compatible. (This code snippet is from the README.md of [vim-one](https://github.com/rakr/vim-one)).

<script src="https://gist.github.com/yifanchen/2168762a8a7cf5b6641e22cc2b7f8f62.js"></script>

Now, you should have something looks like this:

<img src="{{site.url}}/assets/images/correct-vim.png" style="width:50%; display:block; margin:0 auto;">


As you see, the background color of Vim isn't synced up with iTerm background color. So, we will need to sync the Hex Values of both background colors manually. Feel free to use whatever tools you like. I use the eyedropper tool from Photoshop. Screenshot the image, then paste it in Photoshop. Hit the `i`, shortcut of eyedropper tool, then select the color panel, copy the Hex Value of the color.

Now, open your iTerm, hit `cmd` + `,` to open preference setting, go to Profile - Color - Background and paste the Hex Value there. All set.


Now, you Vim should look stunning as you expect it to be.


Certainly, that's not everything. If you use Vim, most likely you use Tmux as well. Let's get the Ture color working in Tmux. First, let's take a look what's going to happen if you don't have True Color enabled in Tmux.

<img src="{{site.url}}/assets/images/wrong-vim.png" style="width:50%; display:block; margin:0 auto;">

Okay, let's get it working right. Check your Tmux version by running:

    tmux -V

If it belows 2.3, run:

    brew upgrade tmux

Now paste the following lines of code into your `.tmux.conf`. (Thanks for the [true color issue](https://github.com/tmux/tmux/issues/34))

<script src="https://gist.github.com/yifanchen/4794061e93923bb4e76f8c9849a53405.js"></script>

Source it, it should look like the lovely sceenshot below. If it doesn't work, you might want to run `tmux kill-server`, then restart the Tmux. I recommend to use [Tmux Resurrect](https://github.com/tmux-plugins/tmux-resurrect) to store your session history, now you can easily restore Tmux session by running `prefix, r`, lovely.

<img src="{{site.url}}/assets/images/final-color-vim.jpg">

Now, you have one of the best-looking Vims fully loaded out there. :)
