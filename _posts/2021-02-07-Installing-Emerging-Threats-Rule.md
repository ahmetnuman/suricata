---
layout: post
title: Installing Emerging Threats Rules on Suricata
tags: Installing Emerging Threats Rules on Suricata
categories: suricata
---

> Ahmet Numan Aytemiz, 7 February 2021

---

- 1. Enable Emerging Threats Rules
- 2. Test Rules

---

#### 1. Enable Emerging Threats Rules

`sudo apt-get install python-pip`

`sudo pip install --upgrade suricata-update`

![Image](/img/pipup.PNG)

`sudo suricata-update update-sources`

![Image](/img/sources.PNG)

`sudo suricata-update list-sources`

![Image](/img/list-sources.PNG)

`sudo suricata-update enable-source et/open`

`sudo suricata-update`

![Image](/img/enable.PNG)

`sudo vim /etc/suricata/suricata.yml`

![Image](/img/vimr.PNG)

#### 2. Test Rules

**Enable Suricata**

`sudo suricata -c /etc/suricata/suricata.yaml -q 0`

**Open Suricata Log File**

`sudo tail -f /var/log/suricata/fast.log`

**Attack From Kali using user agent script scan**

`nmap -p 80 10.0.0.100 --script=http-useragent-tester`

![Image](/img/nmap.PNG)

**Check Suricata Log to Detect this Illegal Scan Activity**

![Image](/img/detected.PNG)

