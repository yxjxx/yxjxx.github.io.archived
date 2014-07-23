---
layout: post
title: Install dropbox in terminal
quote: Sync your life
image: /media/2014-07-23-install-dropbox-in-terminal/dropbox.jpg
---

======================

1. `cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -`
2. `wget https://www.dropbox.com/download?dl=packages/dropbox.py`
3. `sudo cp dropbox.py /usr/local/bin/dropbox`
4. `sudo chmod +x /usr/local/bin/dropbox`
5. `dropbox status`, `dropbox start`, `dropbox status`

---EOF---
