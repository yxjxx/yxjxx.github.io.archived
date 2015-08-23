---
layout: post
date: 2015-08-23 13:10:56 +0800
title: Make capslock act as ctrl
quote: Happy hacking typing!
image: /media/2015-08-23-make-capslock-act-as-ctrl/HHKB_White.jpg
---

Being  a vim user, Ctrl_L is the most used key. But ordinary keyboard's Ctrl is a little hard to press. Sometimes you may want make Capslock act as Ctrl. Here I'll introduce you how to do that in Windows, Linux desktop and Mac.

-----------------------------

Windows7 and later
===============

Download a software named KeyTweak.  
read KeyTweak user's guide In install file folder, you also can find it from Windows start menu by search `keytweak manual`.

Or, you can just download [my config file](https://www.dropbox.com/s/34p8ynaf4cypbg2/keytweak.ktw?dl=0) and import it.

****************************

Mac OS X
===============

Just go to Apple Menu -> System Preferences... -> Keyboard -> Keyboard Tab -> Modifier Keys and select Control for Caps Lock.


-----------------

Linux Mint
===================

Cinnamon
----

Menu-->Perference-->Region & Language -->Keyboard layouts Tab-->downleft corner Options --> Ctrl key position

-------------------

xfce
----

http://software.clapper.org/cheat-sheets/xfce.html  

Option 1: Make the Caps Lock key another control key (with no Caps Lock key)   
`/usr/bin/setxkbmap -option 'ctrl:nocaps'  `  

Option 2: Swap them  
`/usr/bin/setxkbmap -option 'ctrl:swapcaps' `   
Note: setxkbmap is additive. To clear previous set options, use an empty argument first:  

`/usr/bin/setxkbmap -option '' -option 'ctrl:swapcaps'  `
To make sure this happens every time XFCE4 comes up, add an entry to Settings > Session and Startup > Application Autostart.

**Since I haven't used Linux desktop for almost 1 year, the method maybe ineffective.**

------------------

---EOF---

