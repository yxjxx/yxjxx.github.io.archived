---
layout: post
title: Setting pptp vpn
quote: I am no bird; and no net ensnares me. I am a free human being with an independent will. ― Charlotte Brontë, Jane Eyre
image: /media/2014-07-16-setting-pptp-vpn/freedom.jpg
video: false
---

1.

~~~
sudo apt-get install pptpd
~~~

2.

`sudo vim /etc/pptpd.conf` modify

~~~
#localip 192.168.9.1
#remoteip 192.168.0.234-238,192.168.0.245
~~~

to

~~~
localip 192.168.217.1
remoteip 192.168.217.234-238,192.168.217.245
~~~

3.

`sudo vim /etc/ppp/chap-secrets`

add a new line

`<username> pptpd <password> *`

4.

`sudo vim /etc/ppp/options`

add two new lines

~~~
ms-dns 8.8.8.8
ms-dns 8.8.4.4
~~~

5.

`sudo vim /etc/sysctl.conf`

comment out

`net.ipv4.ip_forward=1`

run in terminal `sudo sysctl -p`

6.

`sudo /etc/init.d/pptpd restart`

7.

`sudo apt-get install iptables`

run in terminal

~~~
iptables -t nat -A POSTROUTING -s 192.168.217.0/24 -o eth0 -j MASQUERADE
iptables-save > /etc/iptables.pptp #this line doesn't matter
~~~

`sudo vim /etc/network/if-up.d/iptables`

add content

~~~
#!/bin/sh
iptables-restore < /etc/iptables.pptp
~~~

`sudo chmod +x /etc/network/if-up.d/iptables`

8.

Done, enjoy your hard-earned freedom.