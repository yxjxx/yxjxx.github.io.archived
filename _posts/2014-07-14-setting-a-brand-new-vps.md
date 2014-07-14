---
layout: post
title: Setting a brand new vps
quote: Linode.
image: http://i.v2ex.co/8F61Wb63.png
video: false
---


Assume the ip address is `37.61.54.158`, the username is `yxj`

1. `ssh root@37.61.54.158`
2. `addgroup admin`
3. `useradd -d /home/yxj -s /bin/bash -m yxj`
4. `passwd yxj`
5. `usermod -a -G admin yxj`
6. `sudo vim /etc/sudoers` add a new line `yxj ALL=(ALL:ALL) ALL` under `root ALL=(ALL:ALL) ALL`
7. Test the 6 steps above `ssh yxj@37.61.54.158`
8. At local Machine `ssh-copy-id -i ~/.ssh/id_rsa_pub yxj@37.61.54.158`
9. `sudo vim /etc/ssh/sshd_config`


~~~

Port 24000
PermitRootLogin no
RSAAuthentication yes
PubkeyAuthentication yes
ChallengeResponseAuthentication no
PasswordAuthentication no
UsePAM no

AllowUsers yxj
~~~

10. `sudo service ssh restart`
11. `vim ~/.ssh/config`

~~~
Host s1
    HostName 37.61.54.158
    User yxj
    Port 24000
~~~

12. `sudo apt-get update && sudo apt-get upgrade`
