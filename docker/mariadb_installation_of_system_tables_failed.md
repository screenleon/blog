# Mariadb Installation of System tables failed

> **Lien Chen** *2021-04-23*
I use the smallest lightsail project. I want to use docker to build my website.
When I try to create network with mariadb, the container ran out with installation of system tables failed. 
I use --force-recreate, --no-deps options and rebuild container. It still ran out the error.
In reference, someone said that less of ram may cause this error. So I build mariadb along. Finally, I success build my website.


#### Reference
* [Installation of system tables failed! boot2docker tutum/mysql mount file volume on Mac OS](https://stackoverflow.com/questions/28941175/installation-of-system-tables-failed-boot2docker-tutum-mysql-mount-file-volume)