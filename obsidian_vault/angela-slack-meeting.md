---
type: meeting
topic: work
---

doesn't care if they keep there app server. if they keep it rather they not ssh or scp anything into our server; want them to proxy into it. 
Box would have to come on the inside no matter what (they or we own it; would be happy if they own it so we don't have to redo everything, we'll help them with firewall rules)
first figure out where box will be

web server config should be easy if we can get them (or us) to set up a corresponding server
two web servers. we'd own the one with public stuff (after F5) second one they or us would own it.

apache config server live on same box as app server so they can just cp to different dir instead of ssh-ing. apache would push to public server we own.

firewall rules: sensor IPs and sensor IP
see what the firewall rules currently are for those IPs. ask them if there are currently any firewall rules set up for these IPs.