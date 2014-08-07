---
layout: post
title: Setting IKEV2 for windows phone
quote: Not easy to say love you, my dear Microsoft!
image: /media/2014-08-06-setting-IKEV2-VPN-for-windows-phone/wp_vpn.jpg
---

References:

1. [https://www.v2ex.com/t/126561#reply5](https://www.v2ex.com/t/126561#reply5)
2. [http://lecterlee.com/archives/83](http://lecterlee.com/archives/83
)
3. [https://www.zeitgeist.se/2013/11/22/strongswan-howto-create-your-own-vpn/
](https://www.zeitgeist.se/2013/11/22/strongswan-howto-create-your-own-vpn/)


**Notice: All command is run under ubuntu 14.04.**

1.

`su root`

2.

`apt-get install strongswan*`

3.

run `ipsec version` to verify your installation

4.

###Generate certificate

**Notice: Change the value of CN(in my case: yxjxx.com) to your own domain or ip address**

~~~
ipsec pki --gen --outform pem > caKey.pem
ipsec pki --self --in caKey.pem --dn "C=CH, O=strongSwan, CN=yxjxx.com CA" --ca --outform pem > caCert.pem
ipsec pki --gen --outform pem > serverKey.pem
ipsec pki --pub --in serverKey.pem | ipsec pki --issue --cacert caCert.pem --cakey caKey.pem --dn "C=CH, O=strongSwan, CN=yxjxx.com" --flag serverAuth --outform pem > serverCert.pem
~~~

5.

###move certificate to specified floder

~~~
cp caCert.pem /etc/ipsec.d/cacerts/
cp serverCert.pem /etc/ipsec.d/certs/
cp serverKey.pem /etc/ipsec.d/private/
~~~

6.

`vim /etc/ipsec.conf`

~~~
# ipsec.conf - strongSwan IPsec configuration file

# basic configuration

config setup
    # strictcrlpolicy=yes
     uniqueids = never

# Add connections here.
# Sample VPN connections
#conn sample-self-signed
#      leftsubnet=10.1.0.0/16
#      leftcert=selfCert.der
#      leftsendcert=never
#      right=192.168.0.2
#      rightsubnet=10.2.0.0/16
#      rightcert=peerCert.der
#      auto=start
conn ikev2
        keyexchange=ikev2
        ike=aes256-sha1-modp1024!
        esp=aes256-sha1!
        dpdaction=clear
        dpddelay=300s
        rekey=no
        left=%defaultroute
        leftsubnet=0.0.0.0/0
        leftauth=pubkey
        leftcert=serverCert.pem
        leftid=ikev2
        right=%any
        rightsourceip=10.11.1.0/24   #连接vpn后分配的内网IP网段
        rightauth=eap-mschapv2
        rightsendcert=never
        eap_identity=%any
        auto=add
~~~

7.

`vim /etc/ipsec.secrets`

~~~
# This file holds shared secrets or RSA private keys for authentication.

# RSA private key for this host, authenticating it to any other host
# which knows the public part.  Suitable public keys, for ipsec.conf, DNS,
# or configuration of other implementations, can be extracted conveniently
# with "ipsec showhostkey".
: RSA serverKey.pem
: EAP "123456"  #<your_password> in my case: 123456
~~~

8.

`vim /etc/strongswan.conf`

~~~
# strongswan.conf - strongSwan configuration file
#
# Refer to the strongswan.conf(5) manpage for details
#
# Configuration changes should be made in the included files

charon {
    load_modular = yes
    dns1 = 8.8.8.8
    dns2 = 8.8.4.4
    plugins {
        include strongswan.d/charon/*.conf
    }
}

include strongswan.d/*.conf
~~~

9.

###add iptables rule

~~~
iptables -I INPUT -p udp --dport 500 -j ACCEPT
iptables -I INPUT -p udp --dport 4500 -j ACCEPT
iptables -t nat -I POSTROUTING -s 10.11.1.0/24 -o eth0 -j MASQUERADE
iptables-save
~~~

10.

###start the server

`service strongswan restart`

if service start failed, run `ipsec status` or `ipsec start` may help.


**Server config done**

***********************

11.

###windows phone client config

First you need install certificate caCert.pem which was generated in the server

*Recommand way to transmit the caCert.pem to your phone is to set a nginx server in your server, and use your phone to visit the file's url.*

Detail setting refer link : [http://www.wpapps.com.cn/skill/1150.html](http://www.wpapps.com.cn/skill/1150.html)

username: any username you like, it doesn't matter
password: 123456(set in server's /etc/ipsec.secrets in my case: 123456)

Done!

****************

---EOF---
