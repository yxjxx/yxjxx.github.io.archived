---
layout: post
title: Most Useful cVim Usage Tips
quote: Vim is a lifestyle.
image: /media/2015-10-29-most-useful-cVim-usage-tips/cVim.png
---

## Keybindings

### Movement

same as vim:

~~~
k j h l
u d
gg
G
0
$

~~~

new:

~~~
gi " go to the first input box
Tab " next input box
gI " go to last focused imput box by gi
~~~

### Link hints

~~~
f " open link in current tab
F " open link in new tab
W " open link in new window
mf " open multiple links
mr " multiple google image search with the links
gr " google image search with the link
~~~

### Tab Navigation

~~~
K " next tab
J " previous tab
g0 g$ " first/last tab
x " close the current tab
X " open the last closed tab
H " go back
L " go farword
< > " move current tab left/right
gp " pin/unpin
<C-6> " lastUsedTab, I have mapped it to <C-7>
~~~

### Zoom

~~~
zi
zo
z0
z<Enter> " toggle image zoom (same as clicking the image on image-only pages)
~~~

### URLs Yank

~~~
yy
ya " copy the URLs in the current window
yh " copy the currently matched text from find mode
gy " yank the link to clipboard

p " open the clipboard url
P " open the clipboard url in new tab

~~~


### Search the page

~~~
/ open search bar
n
N
v
V
~~~

### Miscellaneous

~~~
. " repeat the last command
: " open command bar

I " search browser history

gd " :chrome://downloads<CR>
gj " hide the download shelf
gs " view page source

g- " decrement the first number in the URL path (e.g www.example.com/5 => www.example.com/4)
g+


~~~


### cVimrc

examples:

~~~
" enable settings use set
set regexp
set noregexp
let searchlimit = 40
map <C-7> lastUsedTab
~~~

## Links

[Github address](https://github.com/1995eaton/chromium-vim)

[Chrome store](https://chrome.google.com/webstore/detail/cvim/lenndgcmojhcghmfjfneahoeklbjjh)

[Youtube video](https://www.youtube.com/watch?v=7B62wQCmSXM)
