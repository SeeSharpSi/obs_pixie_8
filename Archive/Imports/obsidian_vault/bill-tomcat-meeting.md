---
type: meeting
topic: work
---

# location page for all our apps
* a lot of them are java apps
* java - write code, make it into war file; multiple ways to deploy war file
	* java isn't compiled into binary; it's bytecode
	* we call them gendev, genprod, gentest (gen for general)
	* might still be rare case where it can only work on one app server (usually on two for redundancy)
	* we have tomcat servers (java server)

# tomcat
* when you set war file to run you need .xml file for configs (main thing, you tell it which port to listen on)
* TCP is the dominant network protocol (transport control protocol) [bill shows this](https://en.wikipedia.org/wiki/Internet_protocol_suite)
* GTRI is using a NAT; everything that I go to on GTRI VPN will think he's at the GTRI VPN address
* erouting is always coming in on port 443
* db is port 1521 (rack)
*

CAS:
* when you log in to cas, it has attributes for each user. it will come back to web server and see person has GT account and "title name." like, if you want badge request, it checks that "you better have these perms" (kinda like user groups)
* does CAS req all of the perms or just one of the listed perms?