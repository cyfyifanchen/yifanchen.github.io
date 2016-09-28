---
title: "Swap screenshot shortcuts"
layout: post
date: 2016-03-30
tag:
- Apple
- Shortcuts
- Tips
blog: true
star: false
---

## Swap screenshot shortcuts

We all enjoy using OSX's built-in `cmd` + `shift` + `4` to screenshot. However, it's quite inconvenient to drag and drop the screenshot from desktop every time. Most people don't know that `cmd` + `control` + `shift` + `4` is screenshot directly to the clipboard, the next step is just `cmd` + `v` to any application you like. I found this extremely useful especially when I want to send a screenshot.

Using only left hand to reach 4 keys one time is hard. So I swapped both as in the image below.

![swapping screenshot shortcuts]({{ site.url  }}/assets/images/screenshot-swap.jpg)

Now, sending a screenshot is easy than ever. `cmd`  `shift` + `4` > switch to your chat client > `cmd` + `v`.

## Change format to jpg

Default size of .pngs from screenshots can be huge. That's because the format. Use the following line change it to .jpg, the second is also there in case you want to change it back.

    // change default to .jpg
    defaults write com.apple.screencapture type jpg

    // change back to default
    defaults write com.apple.screencapture type png
