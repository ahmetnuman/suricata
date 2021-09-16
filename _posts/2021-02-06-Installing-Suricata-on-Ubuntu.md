---
layout: post
title: Install Suricata 6.0.0 on Ubuntu 18.04 From Source Codes
tags: Install Suricata 6.0.0 on Ubuntu 18.04 From Source Codes
categories: suricata
---

#### Suricata Getting Started

> Ahmet Numan Aytemiz , 6 February 2021

---
According to Below Topology, i will be ;

- 1. Install Suricata on Ubuntu 18.04 from source code

- 2. Capture First Packet with Suricata
     - Configure Suricata Config File and add two rule two test working suricata (Block inbound tomcat connecion and detect inbound telnet connection)

- 3. Installing Emerging Threats Rules on Suricata
     - Attack From Kali (http user agent script scan)
     - detect this illegal activity with suricata

- 4. Evaluating Suricata Output
    - read eve.json logs with jq much more readable
    - query eve.jsons with jq to filter logs

- 5. Custom HTTP Logging
   
    - enable http logging 
    - verify http logging

     
![Image](/img/labtopologypng.png)

---

## Installation Process

1. **Install Dependencies**
2. **Download and extract Suricata**
3. **Install Recommended Packages**
4. **Compile from source**
5. **Install Suricata**
6. **Verify Suricata Installed**

## 1. Install Dependencies

```
root@ubuntu18:~# apt-get install libpcre3 libpcre3-dbg libpcre3-dev build-essential libpcap-dev libnet1-
dev libyaml-0-2 libyaml-dev pkg-config zlib1g zlib1g-dev libcap-ng-dev libcap-ng0 make libmagic-dev libn
ss3-dev libgeoip-dev liblua5.1-dev libhiredis-dev libevent-dev python-yaml rustc cargo
```

```
root@ubuntu18:~# apt-get install libnetfilter-queue-dev libnetfilter-queue1 libnetfilter-log-dev libnetfilter-log1 libnfnetlink-dev libnfnetlink0
```

```
root@ubuntu18:~# apt-get install libmaxminddb-dev libjansson-dev
```

## 2. Download and Extract Suricata

```
root@ubuntu18:~$ wget https://www.openinfosecfoundation.org/download/suricata-6.0.0.tar.gz
```

```
root@ubuntu18:~# tar -zxvf suricata-6.0.0.tar.gz
```

##3. **Install Recommended Packages**

```
root@ubuntu18:~# cd suricata-6.0.0/

root@ubuntu18:~/suricata-6.0.0# ./configure --disable-gcc-march-native --enable-lua --enable-geoip --enable-nfqueue
```

##4. **Compile from source**

```
root@ubuntu18:~/suricata-6.0.0# make
```

##5. **Install Suricata**

```
root@ubuntu18:~/suricata-6.0.0# make install-full
```

##6. Verify Suricata Installed

```
root@ubuntu18:~# suricata
```

![Image](/img/verify.PNG)
