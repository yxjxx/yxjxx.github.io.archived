---
layout: post
title: Quickly deploy shadowsocks
quote: Hard-earned cyber freedom!
image: /media/2015-01-01-quickly-deploy-shadowsocks/shadowsocks.png
---

References

1. [在 Linode 上快速搭建 Shadowsocks](https://github.com/shadowsocks/shadowsocks/wiki/%E5%9C%A8-Linode-%E4%B8%8A%E5%BF%AB%E9%80%9F%E6%90%AD%E5%BB%BA-Shadowsocks)

--------------

脚本自动安装

~~~
apt-get install curl

curl 'https://raw.githubusercontent.com/shadowsocks/stackscript/master/stackscript.sh?v=4' > /tmp/ss.sh && bash /tmp/ss.sh && rm /tmp/ss.sh
~~~

可能需要用到的命令

~~~
supervisorctl status
supervisorctl tail shadowsocks stderr
cat /etc/shadowsocks.json
supervisorctl restart shadowsocks
~~~

转发到443端口

~~~
< 1024 的端口普通用户没有权限使用，需要用 iptables 转发

sudo iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports 8388
sudo iptables -t nat -A PREROUTING -p udp --dport 443 -j REDIRECT --to-ports 8388
~~~

Shadowsocks multiple ports

Currently Python and Go servers support multiple users. You can use different passwords on different ports like this:

```
{
    "server": "0.0.0.0",
    "port_password": {
        "8381": "foobar1",
        "8382": "foobar2",
        "8383": "foobar3",
        "8384": "foobar4"
    },
    "timeout": 300,
    "method": "aes-256-cfb"
}
```
