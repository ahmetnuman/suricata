---
layout: post
title: Capture First Packet with Suricata
tags: Capture First Packet with Suricata
categories: suricata
---

> Ahmet Numan Aytemiz , 6 February 2021

---

- 1. Suricata Capabilites Overview
- 2. Auto Setup
- 3. Suricata Configuration File
- 4. Inline Mode and IPS Configuration
- 5. Suricata rules file

## 1. Suricata Capabilites

- Capturing Network Traffic For Analysis
- Logging captured traffic for future review
- Generating alerts based on matches to rules
- Intrusion prevention by blocking matching traffic

## 2. Auto Setup

- Auto setup makes life easier
- Completes the configuration actions
- Sets up suricata in a ready run state

## 3. Suricata Configuration File 

(**/etc/suricata/suricata.yml**)

**Contains 5 main sections**;
  - Configure variables
  - Enable outputs
  - Common capture settings
  - App layer protocol configuration
  - Advanced options

#### Explore and Configure Suricata Configuration File for Lab Topology

```
sudo vim /etc/suricata/suricata.yml
```

![Image](/img/homenet.PNG)

#### Inline Mode IPS

```
sudo iptables -I FORWARD -j NFQUEUE
```

#### Suricata Rules 

Suricata rules has 6 portion.

 - Action
 - Protocol
 - Source and Destionation 
 - Ports (source and destination)
 - Direction 
 - Rule Option

 ```
 alert http $EXTERNAL_NET any -> 10.0.0.100 8180 (msg:"Inbound HTTP traffic to Tomcat admin page on port 8180" ; sid:1000001; rev:1;)
 ```

#### Add Basic Rules to Suricata and test it

Test Rules :
 - Block attempts to access Apache Tomcat's admin pages
 - Detect inbound remote access attempts using telnet

`vim /usr/local/share/suricata/rules/local.rules`

![Image](/img/rules.PNG)

`vim /etc/suricata/suricata.yml`

![Image](/img/chn.PNG)

**run inline ips mode**

`sudo iptables -I FORWARD -j NFQUEUE`

**run suricata with ips mode**

`sudo suricata -c /etc/suricata/suricata.yaml -q 0`

![Image](/img/iips.PNG)

**Generate traffic and verfiy suricata logs**

![Image](/img/kali.PNG)

`sudo tail -f /var/log/suricata/fast.log`

![Image](/img/logs.PNG)

**telnet from kali**

![Image](/img/telnet.PNG)

**suricata logs**

`sudo tail -f /var/log/suricata/fast.log`

![Image](/img/telnetlogs.PNG)

