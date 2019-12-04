---
title: "Karabiner Element Config 快捷键神器"
layout: post
date: 2019-08-15
tag:
- dev
blog: true
star: false
---

<span class="fl">之</span>前，一直在用 Keyboard Maestro，好用强大，甚至可以直接 map copy 在 clipboard 上面，trigger 的话，只需要再 map 成不同的 key，而不用再开一个专门记录 copy 的工具，甚至可以 ignore applications，例如，某 keybinding 只在某个 app 里面使用时有效。还可以 input 一个 preference file，以便后续使用。此工具可以说是面面俱到，功能强大。然而，it comes with a price, annually, not a fan.  ¯\_(ツ)_/¯

我在之前的 [ blog ](https://cyfyifanchen.com/advanced-keymapping/) 里面有提到 Karabiner，此神器是位日本大神 Takayama Fumihiko 开源的 project:pray:，2016 年因为 macOS Sierra 的升级，internal keybindings [ TN2450 ](https://developer.apple.com/library/archive/technotes/tn2450/_index.html) 有改，导致当时非常好用的 Karabiner 不再兼容。

<div class="message">Under macOS Sierra 10.12, the mechanism for key remapping was changed. This Technical Note is for developers of key remapping software so that they can update their software to support macOS Sierra 10.12. We present 2 solutions for implementing key remapping functionality for macOS 10.12 in this Technical Note. The command line hidutil tool is useful for executable scripts. macOS applications can use the IOHIDEventSystemClient API to achieve this functionality. The scope of the key remapping function applies to all users and will remain in effect so long as there is an active keyboard service. Key remappings are lost when the system is restarted or if the keyboard service is removed (for example when the last keyboard is disconnected.) No special privileges are required to use key remapping.</div>

后来，大神根据 Sierra 的情况，再次开发了 Karabiner Element，并开源。相比于自带 GUI 的 Keyboard Maestro 来说，虽然 Karabiner Element 需要更加繁琐的配置，但是其性价比则令对手毫无招架之力。所以，不夸张得说，Karabiner Element 可以说是市面上能找到的最好的免费快捷键工具，没有之一 。

此 Post 的目的是一个 walk through，用 Karabiner Element 实现 Keyboard Maestro 的所有功能：

### 需求类目 A：

1. Modifier Flags + key to key

   Use Case: `control` + `h/j/k/l`: `left/up/down/right arrow`.

   Objective: Vi mode-ish navigation.

2. Modifier Flags + key to Modifier Flags + keys

   Use Case: `control` + `command` + `h/j/k/l`: `command` + `left/up/down/right arrow`

    Objective 1: Navigating through beginning and end of a line.

    Objective 2: Navigating top to bottom of a doc.

3. Modifier Flags + Modifier Flags + key to Modifier Flags + Modifier Flags + keys

   Use Case: `control` + `command` + `shift` + `h/j/k/l`: `command` + `shift` + `left/up/down/right arrow`

    Objective 1: Hightlighting through beginning and end of a line.

    Objective 2: Navigating top to bottom of a doc.

### 需求类目 B：

1. Modifier Flags + key to System key

   Use Case: `command` + `shift` + `v`: `clipboard`

   Objective: Tool like Flycut

   Use Case: `command` + `shift` + `f`: `fullscreen`

   Objecrive: Make current app fullscreen with Menu Bar.

好，需求明确了，行动ing。

Karabiner Element 有个 GUI 界面(如下图)，在 Complex Modifications 里面可以 import 现有的 [ rules ](https://pqrs.org/osx/karabiner/complex_modifications/).

<img src="/assets/images/karabiner.jpg">

如此看来，A1 实现起来就 piece of cake 了。那么问题来了，对于在下这种非一般的玩家来说，A2 和 A3 该如何实现呢？:thinking:

先打开已经配置了 A1 的 `.json` 看看：

```json
{
  "title": "Vi Style Arrows",
  "rules": [
      {
          "description": "Change Control + h/j/k/l to Arrows",
          "manipulators": [
              {
                  "type": "basic",
                  "from": <%= from("h", ['control'], ['caps_lock']) %>,
                  "to": <%= to([["left_arrow"]]) %>
              },
              {
                  "type": "basic",
                  "from": <%= from("j", ['control'], ['caps_lock']) %>,
                  "to": <%= to([["down_arrow"]]) %>
              },
              {
                  "type": "basic",
                  "from": <%= from("k", ['control'], ['caps_lock']) %>,
                  "to": <%= to([["up_arrow"]]) %>
              },
              {
                  "type": "basic",
                  "from": <%= from("l", ['control'], ['caps_lock']) %>,
                  "to": <%= to([["right_arrow"]]) %>
              }
          ]
      }
}
```

一目了然，加入对应的 `keycode` 就好，开始ing:

```json
<%# -------------------------------------------------- %>
<%# Change Control + Option + h/l to Option + Left/Right Arrows %>
<%# -------------------------------------------------- %>
{
    "type": "basic",
    "from": < %= from("h", ['control'], ['option']) % > ,
    "to": < %= to([
        [
            ['option'], "left_arrow"
        ]
    ]) % >
},
{
    "type": "basic",
    "from": < %= from("l", ['control'], ['option']) % > ,
    "to": < %= to([
        [
            ['option'], "right_arrow"
        ]
    ]) % >
},

<%# -------------------------------------------------- %>
<%# Change Control + Cammand + Shift + h/l to Command + Shift + Left/Right Arrows %>
<%# -------------------------------------------------- %>
{
    "type": "basic",
    "from": < %= from("h", ['control'], ['shift'], ['command']) % > ,
    "to": < %= to([
        [
            ['option'], ['shift'], "left_arrow"
        ]
    ]) % >
},
{
    "type": "basic",
    "from": < %= from("l", ['control'], ['shfit'], ['command']) % > ,
    "to": < %= to([
        [
            ['option'], [''], "right_arrow"
        ]
    ]) % >
}
```

上面的 Cope Snippet 理论上应工作， 然而， 不工作。:sweat:，好吧，大概是 `syntax` 的问题，得重新去翻翻看 [ doc ](https://pqrs.org/osx/karabiner/document.html#configuration-complex-modifications). Regarding the doc，A2 里面在左右两边都需要 Modifier Flags 的情况并没有被列出来，难道不兼容吗？ :thinking: 这就尴尬了，
我果断决定换下思维模式，先去 Youtube 刷几个韩国女团看看。

我感觉两边都需要 Modifiers Flags 的需求不应该小众到没有，所以，再去看看别人的配置吧，果然有所发现：

```json
"manipulators": [
    {
        "from": {
            "key_code": "h",
            "modifiers": {
                "mandatory": [
                    "control"
                ],
                "optional": [
                    "caps_lock",
                    "command",
                    "option",
                    "shift",
                    "fn"
                ]
            }
        },
        "to": [
            {
                "key_code": "left_arrow"
            }
        ],
        "type": "basic"
    }
]
```

上面的 snippet 就是 A2 和 A3 的实现方式。import 之后，和预期一模一样，完美。

现在来实现，B1, 行动ing.