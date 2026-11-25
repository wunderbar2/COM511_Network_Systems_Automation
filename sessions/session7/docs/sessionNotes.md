[Main Menu](../../../sessions/README.md) |[session7](../../session7/) | [Session 7 Notes](../docs/sessionNotes.md)

# Session 7 Notes

In session 6 we looked at docker compose as an orchestration mechanism for activating applications which use multiple containers.

In this session we will look at two docker compose applications which can help with managing infrastructure.

## OpenNMS

[OpenNMS](https://github.com/opennms/opennms) is an open source network management application which can monitor network and compute infrastructure.
This is a widely used and free monitoring tool which could meet the needs of our customer

Other monitoring applications are also available which you might want to investigate
* [Prometheus](https://prometheus.io/docs/introduction/overview/)
* [Elk - Elastic Search, Log Stash, Kibana](https://www.elastic.co/elastic-stack)
* [Zabbix](https://www.zabbix.com/)

However in our work we will focus on OpenNMS

---
**Exercise 7.1  OpenNMS**

This example is taken from the full set of [OpenNMS tutorials](https://github.com/gallenc/opennms-tutorials-1) which you can review if you wish to take your knowledge further. 

Go through the exercises in  [docker-compose-examples/example7-1](../docker-compose-examples/example7-1).
Make sure you can explain 
* How the Docker Compose script confgures and runs OpenNMS
* How OpenNMS can monitor web sites 
* How OpenNMS can monitor servers and routers using snmp
* Discovering the machines in the lab
* In the networking lab, can you set up a router to repond to SNMP and let OpenNMS scan it?

nimal-minion-activemq> docker compose up -d
[+] up 3/36
 - Image polinux/snmpd [⣿⣀⠀] 13.63MB / 93.32MB                           Pulling                                    9.5s
 - Image docker.io/opennms/minion:33.1.6 [⠀⣷⣿⠀⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀] Pulling                                    9.5s
 - Image docker.io/opennms/horizon:33.1.6                                Pulling                                    9.5s
 - Image docker.io/postgres:15                                           Pulling                                    9.5s
 imal-minion-activemq> docker compose up -d
[+] up 12/12
 ✔ Volume minimal-minion-activemq_data-opennms-cfg Created                                                          0.0s
 ✔ Network minimal-minion-activemq_N000            Created                                                          0.1s
 ✔ Volume minimal-minion-activemq_data-opennms     Created                                                          0.0s
 ✔ Volume minimal-minion-activemq_data-postgres    Created                                                          0.0s
 ✔ Network minimal-minion-activemq_N001            Created                                                          0.1s
 ✔ Container netsnmp_1_1                           Started                                                          2.0s
 ✔ Container netsnmp_1_2                           Started                                                          1.8s
 ✔ Container database                              Started                                                          1.4s
 ✔ Container netsnmp_2_2                           Started                                                          2.4s
 ✔ Container minion1                               Started                                                          2.7s
 ✔ Container netsnmp_2_1                           Started                                                          2.2s
 ✔ Container horizon                               Started                                                          3.0s
then i ran docker compose logs -f horizon
Nodes and their interfaces
172.20.2.1     
172.20.2.1
database.minimal-minion-activemq_N000   
172.20.0.10
_gateway   
172.20.0.1
horizon   
172.20.0.15
localhost     
127.0.0.1
minion-01     
127.0.0.1
minion1     
172.20.2.25
minion1.minimal-minion-activemq_N000   
172.20.0.25
netsnmp_1_1.minimal-minion-activemq_N000   
172.20.0.101
netsnmp_1_2.minimal-minion-activemq_N000   
172.20.0.102
netsnmp_2_1.minimal-minion-activemq_N001     
172.20.2.101
netsnmp_2_2.minimal-minion-activemq_N001     
172.20.2.102
---

## Ansible SemaphoreUI

[Ansible Semaphore UI](https://semaphoreui.com/) is an open source web front end for Ansible which makes it easy to run Ansible scripts from a web UI.

Semaphore makes it possible to schedule or track the manual running of ansible scripts downloaded from a git repository.
If you have predefined Ansible scripts, Semaphore makes it much easier to share them among staff and keep a record of what happens when they are run.


---
**Exercise 7.2  Ansible SemaphoreUI**

Go through the exercises in  [docker-compose-examples/example7-2](../docker-compose-examples/example7-2).
Make sure you can explain 
* How the Docker Compose script runs Ansible SemaphoreUI
* How Ansible Scripts can be run from github using SemaphoreUI
* Can you add an additional ansible project to install a web page on the Apache servers or to do another installation entirely.
---
