---
type: reference
topic: work
---


# start
## ==always `umask 0022`==
* update apps in dashboard
* ![[Pasted image 20240325150001.png]]
* ![[Pasted image 20240326095411.png]]
* do update check 
* ![[Pasted image 20240325150036.png]]
* health check
* ![[Pasted image 20240326095529.png]]
* nagios downtime (host) 
	* schedule downtime for web server (url) 
	* schedule downtime for app server (ssh-ed thing) 
* ![[Pasted image 20240326095033.png]]
* ![[Pasted image 20240325150218.png]]
* `service confluence stop`
* clean up files for storage
	* most files that start w/ a number are a backup (i.e. year, confluence version) 
* ![[Pasted image 20240325150556.png]]
* ![[Pasted image 20240325150707.png]]
* backup inst and home dirs (same as jira) and take vcsa server snapshot 
* ![[Pasted image 20240325151145.png]]
* rsync sharedhome - make sure i am in the previous rsync-ed dir (e.g. 8.7.2-sharedhome.bak) 
* ![[Pasted image 20240325154259.png]]
* do oracle backup 
* run wget-ed installer 
* ![[Pasted image 20240325152221.png]]
* chmod a+x the installer
* ![[Pasted image 20240326101425.png]]
* run the installer in sudo mode 
* ![[Pasted image 20240325152246.png]]
* ![[Pasted image 20240325152442.png]]
* import certs. change setenv.sh and config files. test and prod may require two node number changes (in the same setenv.sh file) 
* do diff between new and old one. Then cp old to new if all looks good AFTER DOING BACKUP OF NEW CONF FILES 
* ![[Pasted image 20240325152640.png]]
* ![[Pasted image 20240325152721.png]]
* confluence doesn't bring over oracle driver, so you need to download it for it to start 
* ![[Pasted image 20240325151722.png]]
* restore con (selinux thing) 
* ![[Pasted image 20240325152910.png]]
* check out troubleshooting and support tools (Amanda does but nice to get some instant feedback) 
* ![[Pasted image 20240325153640.png]]
* also check out "manage apps" for app updates 
* ![[Pasted image 20240326104230.png]]
* no need to re-index unless issue or something 

# notes
* if .tar-ing over copy over the install dir (not the home dir, unless adding a node) 
* don't need to do backups on both sibling servers 
* when taring, just need to change setenv.sh file 
* when several nodes, second node edit Route node# in setenv.sh
* 


Not sure if this was a meeting thing:
I know you're planning to throw me on the upcoming OpenShift GitLab instance (yay!), but feel free to throw me on other apps/upgrades as well. I'm enjoying navigating Linux with the Jira/Confluence upgrades; filesystem and lower level stuff is something I feel like I'd be good at. 