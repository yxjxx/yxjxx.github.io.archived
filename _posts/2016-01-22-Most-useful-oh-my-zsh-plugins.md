---
layout: post
title: 我常用的 oh-my-zsh 插件
quote: Oh My Zsh works best on Mac OS X and Linux.
image: /media/2016-01-22-Most-useful-oh-my-zsh-plugins/ohmyzsh_plugins.png
---

``` 
Oh My Zsh is a way of life! Once installed, your terminal prompt will become the talk of the town or your money back! Each time you interact with your command prompt, you'll be able to take advantage of the hundreds of bundled plugins and pretty themes. Strangers will come up to you in cafés and ask you, "that is amazing. are you some sort of genius?" Finally, you'll begin to get the sort of attention that you always felt that you deserved. ...or maybe you'll just use the time that you saved to start flossing more often.
```

*************

### oh-my-zsh Plugins

终端大概是除了浏览器和 Xcode 之外每天打交道时间最多的软件了。这几年使用 Linux 和 OS X 下来慢慢也是积累了很多工具，这些工具使用好了确实能带来很大的效率提升。我自己其实是一个很健忘的人，一些技巧一段时间不用就忘了，所以在这里写下来备查，有事没事可以看看。今天就来先说说 zsh 和 oh-my-zsh. 关于安装之类的基础操作可以看我写在 wiki 上的当时刚接触时做的[笔记](http://wiki.yxjxx.com/Tool/zsh.html)，本文则重点介绍 oh-my-zsh 的 Plugins.

首先你可以在 oh-my-zsh 的 [github wiki 页面](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins) 查看所有插件列表。当然安装完 oh-my-zsh 之后在你的`~/.oh-my-zsh/plugins` 目录下也有所有的插件。

oh-my-zsh 的 Plugin 安装方式超级简单，你只用修改 `~/.zshrc`文件中的 `plugins=(git python)` 这一行，添加上插件的名字，不同插件之间用空格隔开，然后`source ~/.zshrc`让修改生效即可。

### 目录快速跳转

*[autojump](https://github.com/wting/autojump/wiki)* 启用 autojump，所以还需要单独安装（brew install autojump)。用法是 `j <keyword>`，它会根据你`cd`的历史纪录智能判断你想去到哪个目录，比如我常去`~/Dropbox/dotfiles`，只用`j dot`就好。

我现在在用的是 oh-my-zsh 自带的插件*`z`*，和 autojump 实现的功能是一样的，但是不用额外安装，直接在`plugins=()`里启用就可以了。

### 快速在图形界面中打开目录或文件

*forklift* 在 ForkLift.app 中打开某目录，`fl <dir>`，参数缺省为当前目录效果同`open .`是在 finder 中打开当前目录。

*sublime* 

``` 
st <file> //参数缺省为启动 sublime，与某版本之后 sublime 自带的 subl 命令功能一样
stt <dir> //参数缺省为在 sublime 中打开当前目录，与 `subl .`功能一样
```

### 第三方工具命令补全

这边只列出来我自己在用的几个，其它很多比如 Rails，node，MySQL等也有类似的工具。

*pip* *pod* *brew*

*python* 说是可以给 python 解释器补全，但是我测试不知道为什么不行，不过如果用 iPython 的话，它本身自带补全了。

### Misc.

*sudo* 这可能是我最喜欢的 oh-my-zsh 插件了，它的作用就是连按两下 Esc 键在命令的开头加上或去掉 sudo 关键字

*[zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)* 需要额外安装软件见 [INSTALL.md](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md) 功能是可以高亮 zsh 的关键字。

*history* alias `h` for history and `his <search text>`

*extract* 智能判断压缩包后缀来选择解压命令，再也不用记记了又忘的 tar 的一堆参数了。

*osx*

| Command       | Description                              |
| ------------- | ---------------------------------------- |
| *tab*         | open the current directory in a new tab  |
| _pfd          | return the path of the frontmost Finder window |
| *pfs*         | return the current Finder selection      |
| *cdf*         | cd to the current Finder directory       |
| *pushdf*      | pushd to the current Finder directory    |
| *quick-look*  | quick Look a specified file              |
| *man-preview* | open a specified man page in Preview     |

### git

git 增加了一些系列的 [alias](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugin:git)

| Alias                | Command                                  |
| -------------------- | ---------------------------------------- |
| g                    | git                                      |
| ga                   | git add                                  |
| gaa                  | git add --all                            |
| gapa                 | git add --patch                          |
| gb                   | git branch                               |
| gba                  | git branch -a                            |
| gbda                 | git branch --merged \                    |
| gbl                  | git blame -b -w                          |
| gbnm                 | git branch --no-merged                   |
| gbr                  | git branch --remote                      |
| gbs                  | git bisect                               |
| gbsb                 | git bisect bad                           |
| gbsg                 | git bisect good                          |
| gbsr                 | git bisect reset                         |
| gbss                 | git bisect start                         |
| gc                   | git commit -v                            |
| gc!                  | git commit -v --amend                    |
| gca                  | git commit -v -a                         |
| gcam                 | git commit -a -m                         |
| gca!                 | git commit -v -a --amend                 |
| gcan!                | git commit -v -a -s --no-edit --amend    |
| gcb                  | git checkout -b                          |
| gcf                  | git config --list                        |
| gcl                  | git clone --recursive                    |
| gclean               | git clean -df                            |
| gcm                  | git checkout master                      |
| gcmsg                | git commit -m                            |
| gco                  | git checkout                             |
| gcount               | git shortlog -sn                         |
| gcp                  | git cherry-pick                          |
| gcs                  | git commit -S                            |
| gd                   | git diff                                 |
| gdca                 | git diff --cached                        |
| gdt                  | git diff-tree --no-commit-id --name-only -r |
| gdw                  | git diff --word-diff                     |
| gf                   | git fetch                                |
| gfa                  | git fetch --all --prune                  |
| gfo                  | git fetch origin                         |
| gg                   | git gui citool                           |
| gga                  | git gui citool --amend                   |
| ggpull               | ggl                                      |
| ggpur                | ggu                                      |
| ggpush               | ggp                                      |
| ggsup                | git branch --set-upstream-to = origin/$(current_branch) |
| gignore              | git update-index --assume-unchanged      |
| gignored             | git ls-files -v \                        |
| git-svn-dcommit-push | git svn dcommit && git push github master:svntrunk |
| gk                   | \gitk --all --branches                   |
| gke                  | \gitk --all $(git log -g --pretty = format:%h) |
| gl                   | git pull                                 |
| glg                  | git log --stat --color                   |
| glgg                 | git log --graph --color                  |
| glgga                | git log --graph --decorate --all         |
| glgm                 | git log --graph --max-count = 10         |
| glgp                 | git log --stat --color -p                |
| glo                  | git log --oneline --decorate --color     |
| glog                 | git log --oneline --decorate --color --graph |
| glol                 | git log --graph --pretty = format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit |
| glola                | git log --graph --pretty = format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --all |
| glp                  | _git_log_prettily                        |
| gm                   | git merge                                |
| gmom                 | git merge origin/master                  |
| gmt                  | git mergetool --no-prompt                |
| gmtvim               | git mergetool --no-prompt --tool = vimdiff |
| gmum                 | git merge upstream/master                |
| gp                   | git push                                 |
| gpd                  | git push --dry-run                       |
| gpoat                | git push origin --all && git push origin --tags |
|                      |                                          |
| gpristine            | git reset --hard && git clean -dfx       |
|                      |                                          |
| gpu                  | git push upstream                        |
| gpv                  | git push -v                              |
| gr                   | git remote                               |
| gra                  | git remote add                           |
| grb                  | git rebase                               |
| grba                 | git rebase --abort                       |
| grbc                 | git rebase --continue                    |
| grbi                 | git rebase -i                            |
| grbm                 | git rebase master                        |
| grbs                 | git rebase --skip                        |
| grh                  | git reset HEAD                           |
| grhh                 | git reset HEAD --hard                    |
| grmv                 | git remote rename                        |
| grrm                 | git remote remove                        |
| grset                | git remote set-url                       |
| grt                  | cd $(git rev-parse --show-toplevel \     |
| gru                  | git reset --                             |
| grup                 | git remote update                        |
| grv                  | git remote -v                            |
| gsb                  | git status -sb                           |
| gsd                  | git svn dcommit                          |
| gsi                  | git submodule init                       |
| gsps                 | git show --pretty = short --show-signature |
| gsr                  | git svn rebase                           |
| gss                  | git status -s                            |
| gst                  | git status                               |
| gsta                 | git stash                                |
| gstaa                | git stash apply                          |
| gstd                 | git stash drop                           |
| gstl                 | git stash list                           |
| gstp                 | git stash pop                            |
| gsts                 | git stash show --text                    |
| gsu                  | git submodule update                     |
| gts                  | git tag -s                               |
| gunignore            | git update-index --no-assume-unchanged   |
| gunwip               | git log -n 1 \                           |
| gup                  | git pull --rebase                        |
| gupv                 | git pull --rebase -v                     |
| gvt                  | git verify-tag                           |
| gwch                 | git whatchanged -p --abbrev-commit --pretty = medium |
| gwip                 | git add -A; git rm $(git ls-files --deleted) 2> /dev/null; git commit -m "--wip--" |

其它还有 github gitfast git-extras gitflow,当有空再来研究。

oh-my-zsh 的插件太多，后续遇到好用的插件再来更新。

*To be improved...*