---
title: "Advanced Keymapping"
layout: post
date: 2016-03-20 22:44
tag:
- keymapping
- karabiner
- shotcuts
blog: true
star: false
---

## Advanced Keymapping

In order to get most of this post, please read [OSX-shortcuts-you-might-not-know](http://www.cyfyifanchen.com/osx-shortcuts/) first. 

I am going to talk about how and why I map `hjkl` as `arrow` keys. For the mapping to work, you will need to use either of the following tools. 

[Karabiner](https://pqrs.org/osx/karabiner/): The most powerful key mapping tool. Capable of doing all sorts of crazy key mappings. Preferences come in options,
simply checking option makes configuration even easier. Still unsatisfied? Then make your own `private.xml` and import in. Yes, it is just this amazing. On top of that, 
it comes with a great customer service.(I got response within 8 hours when I sent emails, not to mention the maintainer is in Japan) Most importantly, it is free.

[BetterTouchTool](https://www.boastr.net/): BTT is well known, almost everyone likes the Snap feature, settings are very intuitive. It is no longer free, however spending few bucks to have it 24/7.
I am totally down. In this post, I am not going to show how BTT works, it's very easy to figure out.

Between these two tools, I would go with Karabiner over BTT for two reasons:

1. Unlike `arrow` keys, `letter` keys don't repeat themselves when holding down in OSX(Windows does),
which could be annoying. Luckily, Karabiner fixes this problem.

2. Free.

### About HJKL

I started to use Vim last year. I absolutely like model editing and the idea of mouse-less. `hjkl` is one of the most beautiful inventions in Vim. 
I wanted to apply the idea to the entire system. It turned out better than I thought. Now I use it for everything, checking out emails in Mail, browsing files in Finder,
going through lists in Slack, etc. 

The screen shot is my setting. You are welcome to play with it, map any way you like. I am going to use my mapping as an example.

![Karabiner key mapping](http://www.cyfyifanchen.com/assets/images/karabiner-setting.jpg) 

After you map it the way like I do, the beautiful part happens:

`control` + `h` + `j` + `k` + `l`: `left` `down` `up` `right`.

`control` + `cmd` + `h` or `l`: navigating through beginning and end of a line.

`control` + `cmd` + `shift` + `h` or `l`: select entire line.

`control` + `cmd` + `k` or `j`: top or bottom of the file

`control` + `cmd` + `shift` + `k` or `j`: select entire file from either top or bottom.

`control` + `j` and `control` + `k`: going through intellisense in IDE or up and down when search in Google.

`control` + `l`: very useful to attach parameters to the end of a url.

##### Example of adding a parameter to an url with both hands on row 2 of keyboard.

1. `cmd` + `l` 
2. `control` + `l`
3. type the parameter.

Now, you can navigate through lines of code without moving right hand to `arrow` keys.


##### What if I already mapped `control` + `hjkl` in Vim?

1. I suggest to disable Karabiner when iTerm is running. Why? Because Vim comes with powerful shortcuts, we should learn them.
2. `fn` + `hjkl`


##### Map `caps lock` to `control` smartly

Instead of mapping `caps lock` to `control` permanently, why don't just map it only when `caps lock` is holding down with other keys?
Use [Seil](https://pqrs.org/osx/karabiner/seil.html.en) to do it.

### Conclusion 

This post is meant to share my key mappings, shortcuts and how I benefit from them, I am sure there are far more than I know.
With good software, be creative with your own mappings.

# 中文

可能是原来玩魔兽的原因，一直喜欢玩快捷键，能用快捷键的地方尽量不用鼠标点击。现在所有工作用一个MacBook Pro来完成，不需要任何外接显示器。熟知快捷键工作效率高，同时乐趣也多。
玩vim有感，觉得`hjkl`做为方向键再合适不过了。编辑的时候，光标可以左右移动，无论是拷贝复制，还是整段的代码选择，都会方便非常多。试过之后，是如此好用。
这里简单介绍两个快捷键编辑器：

[Karabiner](https://pqrs.org/osx/karabiner/): 是可以找到的最强大的编辑器，没有之一。功能多的让人头痛。最厉害的是什么都帮你想好了，只需要选择喜欢的选项就可以。

[BetterTouchTool](https://www.boastr.net/): BTT 也是个非常出色的软件，简单易用。

如果你也喜欢快捷键，并且是按我的设置来的话（如图），下面这些快捷键组合会让你幸福感暴增。

`control` + `h` + `j` + `k` + `l`: 左，下，上，右。

`control` + `cmd` + `h` or `l`: 到整行的开始或者末尾。

`control` + `cmd` + `shift` + `h` or `l`: 选择整行。

`control` + `cmd` + `k` or `j`: 文件的最开始和结尾。

`control` + `cmd` + `shift` + `k` or `j`: 选择所有文件内容。

`control` + `j` and `control` + `k`: 这个在百度搜索东西的时候上下选择很有用。

`control` + `l`: 这个在网址地址太长不想打而又需要在末尾加参数的时候用最合适不过了。

##### 实例演示，如何快速地在网址末尾加参数

1. 打开浏览器
2. `cmd` + `l` 
3. 打入地址，如果地址很长，会自动选择。
4. `control` + `l`
5. 打入参数

整个过程手不需要离开键盘的黄金位置。

##### 如果在vim里面我已经设置了'control' + `hjkl` 怎么办？

1. 我建议disable karabiner用vim的时候，为什么？很简单，vim的快捷键很强大，必须去发觉。
2. `fn` + `hjkl`

### 总结

最后，这个post的目的是分享快捷键的小技巧，当然你可以按自己的方式来。
