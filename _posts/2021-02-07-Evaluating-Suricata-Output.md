---
layout: post
title: Evaluating Suricata Output
tags: Evaluating Suricata Output
categories: suricata
---

> Ahmet Numan Aytemiz, 7 February 2021

---

#### Suricata Output Options

- **EVE JSON**
- **Lua**
- **Syslog**
- **Custom HTTP**
- **Custom TLS**

#### EVE JSON Log File

**Eve Json output file is**;

   - Extensible Event Format (eve) event log
   - Uses json output format to log actions
   - supports all alerts, anomalies, metadata, file information, and protocol specific records

**Output collected in EVE**;

   - **Alerts**
   - **Anomalies**
   - **HTTP**
   - **DNS**
   - **TLS**

**Reading and extracting Information**;

   - Manually read through the logs
   - Leverage third party applications like JQ and ELK

##Lab : Explore the EVE.JSON the Use JQ to query EVE.JSON

without JQ it is very diffucult to read eve.json log file as follow;

`sudo cat /var/log/suricata/eve.json`

![Image](/img/eve.PNG)

**Install JQ**

 `sudo apt-get install jq`

 **Using jq we can much eaiser read eve json file**

`sudo cat /var/log/suricata/eve.json | jq`

![Image](/img/jq.PNG)

**We can query logs with jq**

`sudo cat /var/log/suricata/eve.json | jq 'select (.event_type == "alert")'`

`sudo cat /var/log/suricata/eve.json | jq 'select (.event_type == "alert") | [.timestamp, .src_ip, .dest_ip, dest_port, alert]'`

`cat /var/log/suricata/eve.json | jq -c 'select(.alert.signature_id == '1000002') | [.timestamp, .src_ip, .dest_ip, .dest_port, .alert]'`

