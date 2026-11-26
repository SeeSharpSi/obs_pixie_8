---
type: meeting
topic: work
---

# **DON'T MENTION CYBER INCIDENT**
# Meeting w/ Wes & Angela
measures lightning strikes
it talks to national weather service
we need to get it underneath true IT web service control

it's currently under the 132 07 193 (public internet)

want this in less than a month

apache web server. just shows a bunch of .png pictures (generates through cron job, ships to web server, that's what people view).
There may be some resistance to this being moved (politics ez)

Only complicated part is that all the data is communicating over verizon or tmobile to send lightning strike data home. Firewall rules through IOT (should maybe be through GTRI) so may be Firewall rules set up to allow them to talk.

don't mix with tomcat server. Not sure what server this is being put on. will probably have redundancy. "would be cool but start with single one"

-> ideally would have web server on external and it would talk to the app server (box under guy's desk). Box under desk needs to be on internal server.

# Knowns
* North Georgia Lightning Mapping Array (NGLMA)

# assumptions
* Java program gets data input, exports single .png (or an array of)
* Cron job runs the program every ? minutes (website says "latest 10 minutes summaries" so 10min is good assumption)
* Java program probably doesn't connect to the internet itself. The .tgz file in Box seems to be how it connects to the outside world.

# Questions
* Does Java send .png to external website, or does Cron?
* How is it being sent? (http, several packets...? what protocols?)
* What exactly is on the box? _Just_ the Java app, or more? Is it what's in the DropBox folder?
* What kind of server should we set up? How many gigs of ram, cpu, etc.?
* They have SSL set up. How will that need changed?
* How do devices send info to your server? What kind of Firewall "stuff"/rules are set up?

# Firewall
* What needs opened? Broad question, but yeah
* How will the firewall affect the program? (change apache config, change Java endpoints, etc.)

# More
* "the one part that kind of worries me is the devices that send the data to his server.  John said he had some FW rules set up, so we'd have to duplicate them.  Well, not really worried about them, just have to make sure we get that set up for wherever the server would go."


You have an application that runs a server that interfaces with external things. And we're moving that server from the IOT to our internal DMZ.

How are things sent to your server? How is the firewall set up around this?
# Meeting

## Question Answers

## Firewall
Could make firewall rule for his server's ip address (jailed scp sessions sftp subproccess of ssh jail user to specific location) can write a rule to jail user (only if using sftp process) allow specific user specific access to http location, can't access other ips.
Jail john's account to his html directory so that if his server gets compromised they can't access anything, other than john's website.

Try setting up server with jailed ssh account. Try to scp into it (should get error) but try to sftp into it and it works (but can only access jailed things).


# Meeting v2
Chris mentioned making a "jailed sftp user," which is a good idea. Though we'll ultimately need the server on our internal network, either way.

Application retrieves stuff from external source. Uses it to make .pngs, sends .pngs to internal/external website?

little sensors in the field that all collect data. sends it back to server computer that sits under john's desk in cobb county dmz. archives data, takes data and creates maps or sources of lightning over north georgia and creates image. takes the last 20 minutes of images to server that's publically accessible (ajax script takes images and creates simple animation). those sensors need to be the exception in the firewall (12 ip addresses).
Problem is the sensors need to send data to john's dmz (.130.207.???.136) without it being on public network. john's sever also needs way to push images to public website while remaining on internal gtri network.

nglma hosts; that's the one that sits under his desk. .136 machine. On DMZ. Only firewall exception is the sensors. It makes the images but can't send them (used to send them to seal webmail).
John concern with nglma host is that he has sensors in field programmed rn to send data over ssh tunnels to nglma. Can set it up but if they lose track they'll have to default to something with static ip address.
first thing is getting web page up again (where does he push the files (images, script, static webpage) so people can see it). the webserver is just offline right now.
as long as john can scp to something from nglma host he's good.
he has machine called nglma-host (136 machine). sends image out to whatever webserver.
we need new home for john's nglma website.
step two is upgrading nglma host (ubuntu server).
Mentioned John's server having completely public stuff.
Best protocol for pushing from John's server to external server.
if it's a fixed address it can be internal
nglma-host is recieving data from sailor networks (verizon and such)
give john more money so he can fix anything (specifically making the server pull from the sensors instead of them pushing it to him)
gmf is mac
ubuntu is landscape
redhat is sattelite
"If john's server can upload its web files to your server via sftp jail does that work? and by using sftp it's a subprocesses of the open ssh server; it can't run shell commands to the server. Can only use ftp command."


# Flow of servers
* Sensors in field push data to John's box (.136) over sailor networks (Verizon, t-mobile, etc.)
* John's box creates images with sensor data
* John's box sends images to publicly accessible webserver/website

# Servers

## John's Box / nglma-host
* Is on .136; says it's on Cobb County DMZ.
* Only firewall exceptions are sensor IPs (12 of them)
* Uses scp to send data. Will probably change over to ftp/sftp
* Uses ssh tunnel to pass data from sensors to John's box

## Public Website
* Doesn't currently exist / is down
* John needs something the public can access

# John's needs/worries
* Needs a new public-facing webserver to push files to for people to view (images, ajax script, static webpage)
* Worried about sensors in field. They need a static ip to send data to.
* Wonders how he can send data from internal box to external web server.

# sftp/ssh jailing
Chris mentioned the ability to jail a Linux user to a specific directory, only allowing sftp calls inside of that directory. Very few security concerns; sftp is a subprocess and doesn't spawn a shell (unlike scp) meaning an exploit through that venue would only allow ftp calls in the specified directory.
This could be a useful way to securely transfer files from John's box to the public website. [Here's](https://access.redhat.com/solutions/2399571) a basic how to do this, though I've not yet tested it.
Chris' question:
"If john's server can upload its web files to your server via sftp jail does that work? and by using sftp it's a subprocesses of the open ssh server; it can't run shell commands to the server. Can only use ftp command."

# Field Sensors
John isn't sure how to get his field sensors to send data to an internal server. He mentioned reversing the tunnels, having his server pull from the sensors instead of them pushing.
Can John use a static IP for his box on our internal servers? That might make it easier.