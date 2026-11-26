---
type: meeting
topic: work
---

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