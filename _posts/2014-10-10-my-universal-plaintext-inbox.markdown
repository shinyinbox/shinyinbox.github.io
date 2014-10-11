---
layout: post
title:  "My Universal Plaintext Inbox"
date:   2014-10-10 12:00:00
tags: [Inbox, Keyboard Maestro, Drafts, Popclip]
---
Ubiquitous capture of information is an important part of my workflow. Quick Entry shortcuts in task managers like [Things](https://culturedcode.com/things/) and [OmniFocus](https://www.omnigroup.com/omnifocus) make capturing tasks frictionless when I'm at my Mac. For more general information capture, I've hacked together a bunch of ways to quickly get text into a single place: a plaintext file called "Inbox.txt."

**The syncing setup:** The Inbox.txt file is located in my [nvALT](http://brettterpstra.com/projects/nvalt/) folder in Dropbox, and I sync to that same folder in [Editorial](http://omz-software.com/editorial/) on iOS. Because I sort files by date in both apps, and because I add to the file frequently, it generally stays towards the top. I have three methods for quickly adding text to the file, but they all result in the same format including a date stamp below it.

 <p style="text-align: center;"><img src="/images/2014-10-10-my-universal-plaintext-inbox-1.png" alt="Inbox in nvALT and Editorial" /></p>

**The Keyboard Maestro macro:** Not being a programmer, I rely on [Keyboard Maestro](http://keyboardmaestro.com/) to hack together what I'm not skilled enough to do more elegantly. This macro is no exception.

 <p style="text-align: center;"><img src="/images/2014-10-10-my-universal-plaintext-inbox-2.png" alt="Add to Inbox Keyboard Maestro macro" /></p>

Hitting **Control + Option + Command + I** brings up a simple text entry field. The clipboard is prefilled, so hitting return will immediately add that to the Inbox. It also opens with the clipboard text selected, so you can start typing without worrying about clearing the contents of the field. Hit return and the text is entered. Behind the scenes, the macro reads the contents of the current Inbox.txt file to a variable, then prepends the inputted text along with a date stamp.

 <p style="text-align: center;"><img src="/images/2014-10-10-my-universal-plaintext-inbox-3.png" alt="Add to Inbox Keyboard Maestro text entry field" /></p>

**The PopClip extension:** [PopClip](http://pilotmoon.com/popclip/) lets you do things with selected text faster than anything I've seen. I frequently use it to do a Google search on selected text, copy text, or open a selected link. It occurred to me that I could make my Inbox text entry even faster by making a PopClip extension to send the selected text to the Inbox. Because I am not a programmer, I opted for a simpler solution than writing a complete PopClip extension (which I'm sure is both possible and more elegant). Instead, I made a very simple PopClip extension called "Inbox" that performed the singular task of firing off a keyboard shortcut that then triggered a Keyboard Maestro macro. Sounds convoluted, but it has worked flawlessly for me, was much quicker to implement, and a lot easier to tweak as needed, by using the familiar and accessible Keyboard Maestro interface. The PopClip extension contains only the required Config.plist file and the following super-short AppleScript:

<p style="text-align: center;"><img src="/images/2014-10-10-my-universal-plaintext-inbox-4.png" alt="PopClip AppleScript" /></p>

Selecting any text on my system brings up the following PopClip options:

<p style="text-align: center;"><img src="/images/2014-10-10-my-universal-plaintext-inbox-5.png" alt="PopClip Inbox Extension" /></p>

Clicking on "Inbox" sends the selected text or link to my Inbox.txt file via the following Keyboard Maestro macro: 

<p style="text-align: center;"><img src="/images/2014-10-10-my-universal-plaintext-inbox-6.png" alt="PopClip Keyboard Maestro macro for Inbox" /></p>

**The Drafts Action:** By far, the easier piece of this system was setting an action in the amazing [Drafts](http://agiletortoise.com/drafts/) app for iOS. The custom Dropbox action was made as shown below, and executed by selecting the "Inbox" action.

<p style="text-align: center;"><img src="/images/2014-10-10-my-universal-plaintext-inbox-7.png" alt="PopClip Keyboard Maestro macro for Inbox" /></p>

So that's it! Took some time (okay, lots) to set up, but I use it all the time, especially the PopClip extension and Drafts action. Having this single inbox for capture of random information (text, links, quotes, code snippets, telephone numbers, reminders) is a big relief, because I can trust that when I send something there, I will always know where to find it. Plus it's stored in plaintext, and recent versions are accessible on Dropbox and on TimeMachine.