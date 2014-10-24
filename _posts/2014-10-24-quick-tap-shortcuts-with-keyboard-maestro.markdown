---
layout: post
title:  "Quick-Tap Shortcuts with Keyboard Maestro"
date:   2014-10-24 7:00:00
tags: [Keyboard Maestro, Shortcuts]
---
As an avid keyboard shortcut user, I learn the default shortcuts for commands I frequently use and create custom shortcuts for other functions. It doesn't take long before you run out of convenient, easy to muscle-remember shortcuts. [Brett Terpstra](http://brettterpstra.com/2012/12/08/a-useful-caps-lock-key/) and [Steve Losh](http://stevelosh.com/blog/2012/10/a-modern-space-cadet/) inspired me to experiment with new types of shortcuts. I wanted to avoid installing kernel extensions, so I came up with some solutions using only [Keyboard Maestro](http://keyboardmaestro.com/).

Modifier keys like `Option` and `Shift` don't perform actions by themselves, so I set these up as **"Quick-Tap Shortcuts"** using the following [macro](/files/2014-10-24-quicktapshortcutmacro.kmmacros):

![Quick Tap Shortcut in Keyboard Maestro](/images/2014-10-24-quick-tap-shortcuts-with-keyboard-maestro.png)

This macro exploits the `device key` trigger in Keyboard Maestro, which differs from a hot key in that it merely observes that a physical key has been tapped, and does not interfere with it's function. In this case, whenever the `Left Option` key is pressed, the macro pauses for 0.1 seconds, then checks to see if the key is **still** being pressed. If it's not (meaning the key was tapped quickly), it triggers the desired action, in this case toggling the Finder. Having this short of a time limit ensures that only a brief tap of the key will activate the macro, but using the key in another shortcut, for instance `Option + Space` (which for me activates my clipboard history), will not.

Because the device key trigger sees the left and right versions of keys as distinct, you can create 8 or 9 quick-tap shortcut keys that each perform a custom action, while still being able to use those keys as you normally do.

*Tip: I avoid using the `Left Command` key for this purpose, as I use it so frequently in other hot key commands. I sometimes hit `Command + Space` so quickly (in less than 0.1 seconds) that it causes a conflict.*