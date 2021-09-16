---
layout: post
title: Custom HTTP Logging
tags: Custom HTTP Logging
categories: suricata
---

> Ahmet Numan Aytemiz, 7 February 2021

---

## Custom HTTP Logging

- Log HTTP transactions to a file
- Capture HTTP header, request, method and URL
- Customize alert string format

## Custom TLS Logging

- Log TLS transactions to a seperate file
- Customize TLS Log format
- Log certificate issuer and subject

## Custom HTTP Logs Lab

- Enable HTTP logs
- Send test traffic to the internal network
- Explore the HTTP Logs

**Enable HTTP Logs**

`sudo vim /etc/suricata/suricata.yml`

![Image](/img/format.PNG)

####Verify HTTP Logging

**Sample Request from Kali To Metasploitable**

![Image](/img/reqe.PNG)

**Verify HTTP Logs on Suricata**

`sudo tail -f /var/log/suricata/http.log`

![Image](/img/httplog.PNG)
