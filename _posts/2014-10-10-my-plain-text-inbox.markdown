---
layout: post
title:  "My Plain Text Inbox"
date:   2014-10-10 12:00:00
tags: [Inbox, Keyboard Maestro, Drafts, PopClip]
---
Quickly capturing information is an important part of my workflow. Quick Entry shortcuts in task managers like [Things](https://culturedcode.com/things/) and [OmniFocus](https://www.omnigroup.com/omnifocus) make capturing tasks frictionless when I'm at my Mac. For more general information capture (text, links, quotes, code snippets, telephone numbers), I've hacked together a bunch of ways to quickly get text into a single place: a plain text file called "Inbox.txt" synced in Dropbox.

**The syncing setup:** The Inbox.txt file is located in my [nvALT](http://brettterpstra.com/projects/nvalt/) folder in Dropbox, which I also sync to in [Editorial](http://omz-software.com/editorial/) on iOS. Because I sort files by date in both apps, and because I add to the file frequently, it generally stays towards the top. I have three methods for quickly adding text to the file, but they all result in the same format with a timestamp below it.
 
 ![Inbox in nvALT and Editorial](/images/2014-10-10-my-plain-text-inbox-1.png)

**The Keyboard Maestro macro:** Not being a programmer, I rely on [Keyboard Maestro](http://keyboardmaestro.com/) to hack together what I'm not skilled enough to do more elegantly. This macro is no exception:

![Add to Inbox Keyboard Maestro macro](/images/2014-10-10-my-plain-text-inbox-2.png)

Hitting **Control + Option + Command + I** brings up a text entry field. The clipboard is pre-filled, so hitting return will add that to the Inbox. It also opens with the clipboard text selected, so you can start typing right away, without clearing the contents of the field. Hit return and the text is entered. Behind the scenes, the macro reads the contents of the current Inbox.txt file to a variable, then prepends the inputted text along with a timestamp.

![Add to Inbox Keyboard Maestro text entry field](/images/2014-10-10-my-plain-text-inbox-3.png)

**The PopClip extension:** [PopClip](http://pilotmoon.com/popclip/) is one of the fastest ways to do something with selected text. I frequently use it to do a Google search on selected text, copy text, or open a selected link. It occurred to me that I could make my Inbox text entry faster by making a PopClip extension to send the selected text to the Inbox. Because I am not a programmer, I opted for a simpler solution than writing a complete PopClip extension (which I'm sure is both possible and more elegant). Instead, I made a very simple PopClip extension called "Inbox" that performed the singular task of firing off a keyboard shortcut that then triggered a Keyboard Maestro macro. Sounds convoluted, but it has worked flawlessly for me, was easy to implement, and was easy to tweak in the familiar and accessible Keyboard Maestro interface. The PopClip extension contains only the required Config.plist file and the following super-short AppleScript:

![PopClip AppleScript](/images/2014-10-10-my-plain-text-inbox-4.png)

Selecting any text on my system brings up the following PopClip options:

![PopClip Inbox Extension](/images/2014-10-10-my-plain-text-inbox-5.png)

Clicking "Inbox" sends the selected text or link to my Inbox.txt file via the following Keyboard Maestro macro: 

![PopClip Keyboard Maestro macro for Inbox](/images/2014-10-10-my-plain-text-inbox-6.png)

**The Drafts Action:** By far, the easiest piece of this system was setting up an action in the amazing [Drafts](http://agiletortoise.com/drafts/) app for iOS. The custom Dropbox action was made as shown below, and executed by selecting the "Inbox" action.

![Drafts Action for Inbox](/images/2014-10-10-my-plain-text-inbox-7.png)

So that's it! Took some time (okay, lots) to set up, but I use it all the time, especially the PopClip extension and Drafts action. Having this single inbox for capturing random information has stuck with me because I know that when I send something there, I will always be able to find it. Plus it's stored in plain text, and older versions are backed up on Dropbox and TimeMachine.