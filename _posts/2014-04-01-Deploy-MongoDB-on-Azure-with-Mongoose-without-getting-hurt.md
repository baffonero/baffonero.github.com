---
layout: post
category : blog
tagline: "Supporting tagline"
tags : [food, meetings]
---

Symptoms
----------------------------

Last month we moved our MongoDB instance to a Linux Virtual Server on Windows Azure.
I think Windows Azure is a great platform but I am also convinced that a second after registration there should be someone who asks you: 

**"Do you know what TCP_KEEPALIVE_TIME is? Are you sure? Are you really really sure you do?"**

Well, if you don't you'll notice that your node long running application will start crashing in this sweet fashion:


	"uncaughtException: failed to connect to [your.damned.machine: 27017]\nstack: \nError: failed to connect to [your.damned.machine:: 27017]\n at Ser [...]"


Why? 
-----------------------------

The name of your enemy is "IDLE TIMEOUT"

Luckily, there are people in the world who have had your own bad luck before and can prevent you from banging your head against the wall for days.


The Cure 
-----------------------------

If you are in the same situation be sure to check 2 thing:

1. Mongoose Version

Be sure to run at least Mongoose 3.6.15

2. Tune TCP_KEEPALIVE_TIME

Display current value (default values is usually 7200)

	root@yourserver:~# sysctl net.ipv4.tcp_keepalive_time
	net.ipv4.tcp_keepalive_time = 7200 // seconds

Change TCP_KEEPALIVE_TIME value:	

	root@yourserver:~# sysctl -w net.ipv4.tcp_keepalive_time=30
	net.ipv4.tcp_keepalive_time = 30

If you too have had huge adrenaline rushes seeing your application crashing over and over in production again and again


Futher reading:
[Using TCP keepalive under Linux](http://tldp.org/HOWTO/TCP-Keepalive-HOWTO/usingkeepalive.html)
