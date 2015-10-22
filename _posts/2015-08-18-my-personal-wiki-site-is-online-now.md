---
layout: post
title: My personal wiki site is online now
quote: Manage your knowledge like a pro!
image: /media/2015-08-18-my-personal-wiki-site-is-online-now/Amazing_Crystal_blue_water__i.imgur.com_.jpg
---

[My personal wiki, powered by simiki.](http://wiki.yxjxx.com)

*************

1. Build with [Simiki](http://simiki.org/)
2. [Quick Start](http://simiki.org/docs/)
3. [Deploy it to Github Pages](http://simiki.org/docs/deploy.html)
4. My Best Practice

~~~
cd mywiki
simiki new -t "your wiki's title" -c "your wiki's category"
//Write something useful.
git add "related files"
git commit -m "commit message"
git push -u origin master
simike generate
//push output/ to gh-pages brance
cd output/
git add .
git commit -m "commit message"
git push -u origin gh-pages
//go to your website, your content will be there.(maybe several minutes later)
~~~

**********

**Your can find my whole wiki repo in [github](https://github.com/yxjxx/wiki.yxjxx.com).**
