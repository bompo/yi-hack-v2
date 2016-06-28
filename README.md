===============
Yi-hack-v2 project
===============

Special thanks go to fritz-smh : https://github.com/fritz-smh/yi-hack

This Yi-hack-v2 project is totally inspired from its own project.


Purpose
=======

This project is a collection of scripts and binaries file to hack your Xiaomi Yi Ants Camera 2.

![Alt text](yi-v2.png?raw=true "Yi Ants Camera 2")

This camera has the default following features :
* wifi
* motion detection : a video file is generated if a motion have been detected in the last 60 seconds.
* send video data over the network on Chinese servers in the cloud to allow people to view camera data from their smartphone wherever they are.
* setup thanks to a smartphone application.
* local video storage on a SD card
* no RTSP server

This hack includes :
* Base firmware : 2.1.1_20160429113900
* Telnet server activated
* FTP server activated
* Ability to choose voice between Chinese, English and French

Warning about some models that are usable only in China
=======================================================

My camera is a CN model, thus it can't be paired with a smartphone outside China. Thanks to https://diy.2pmc.net/solved-xiaomi-xiao-yi-ant-home-camera-can-used-china/ an old firmware (2.1.1_20160429113900) is available and make this CN model pairable with an Android device app (http://app.mi.com/detail/75646). The firmware comes from http://yi-version.qiniudn.com/@/familymonitor-h21/2.1.1_20160429113900home

Installation on the Yi camera
=============================

The memory card must stay in the camera ! If you remove it, the camera will start without using the hack.

Prepare the memory card
-----------------------

Clone this repository on a computer :

    git clone http://github.com/niclet/yi-hack-v2.git
    
Then, format a micro SD card in fat32 (vfat) format and copy the content of the **yi-hack-v2/sd/** folder at the root of your memory card.

The memory card will so contain :

* home.bin : the official firmware file compliant with CN model
* test : the folder which contains the hack scripts and binaries

Start the camera
----------------

* If plugged, unplug the Yi camera
* Insert the memory card in the Yi camera
* Plug the Yi camera
* Follow english instructions to pair with your android app. This is only needed the first time.

The camera will start. The led will indicate the current status :
* yellow : camera startup
* blue blinking : network configuration in progress (connec to wifi, set up the IP address)
* blue : network configuration is OK. Camera is ready to use.

How can I know which is the version of a firmware 'home.bin' file ?
===============================================================

Just do : **strings home.bin | grep YUNYI_VERSION**. Example :

    $ strings home.bin | grep YUNYI_VERSION
    YUNYI_VERSION=2.1.1_20160429113900


Use the camera
==============

Telnet server
-------------

The telnet server is on port 23.

No authentication is needed, default user is root.

Ftp server
----------

The ftp server is on port 21.

No authentication is needed, you can use anonymouse user.


I want more !
=============

For now, it is just a kind of proof of concept. Many work has still to be done.

Coming soon !
=============

Connection to wifi without Android app is in progress.
RTSP server is also in progress, this will be the more important and difficult part.


How it works ?
==============

Hack content
------------

````
home.bin                       Official firmware 2.1.1_20160429113900
test/                          Yi hack folder
  factory_test.sh              This script is called on camera startup and will launch all the needed processes
  factory_test.log             Log file of the hack (filled by factory_test.sh)
  v2/
    bin/
      tcpsvd                   TCP Service Daemon (http://smarden.org/ipsvd/index.html) to launch FTP Server (ftpd)
      yihackv2.so              Native library to provide hacked features
    audio/
      fr/
        *                      French voice files
````


factory_test.sh
---------------

**TODO**
