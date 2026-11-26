---
type: reference
topic: work
---

* always remember `umask 0022`
* `service jira stop`
* backup jira installation, home, and sharedhome dirs
* ![[Pasted image 20240321154053.png]]
* 

# q/a
* `helpdesk` is the ESD instance of Jira (so "ESD Jira" is this instance; Raj likes his urls)
* CR = Change Request 

# cr
![[Pasted image 20240322140028.png]]
![[Pasted image 20240322140211.png]]
Put myself as team lead
Amanda system tester
![[Pasted image 20240322140712.png]]
^ this doesn't matter too much, just pick Prod or side
![[Pasted image 20240322140932.png]]

# start
manage apps
	update the apps that need an update

# nagios
instance management
	scheduled downtime
![[Pasted image 20240322142054.png]]

# stop jira
`service jira stop`
then only upgrade service ending in "1" and copy-paste files over to other one

# oracle backup
![[Pasted image 20240322142751.png]]
two databases
once we make it where we contact DBAs we'll make it so we contact them and tell them which database(s) to backup

# backups
![[Pasted image 20240322143354.png]]
rsync is a diff, so can run once early in the day before backing up so that when doing it at night it's faster

# run .bin 
![[Pasted image 20240322145423.png]]
![[Pasted image 20240322145715.png]]


# cmd things
esc+k
cw (vim thingy for change word)


also copy new files before doing diff

`restorecon -R -v /app/atlassian/` is good to run all day long (it's an selinux file perm thing)

# tar files to be moved 
ACTUALLY DON'T COPY `home` (we WANT install, we DO NOT WANT home)
before using tar files make backup of whatever files I'm replacing
![[Pasted image 20240322151232.png]]
![[Pasted image 20240322154043.png]]
then do the same for jirainst

then change the `Route` node var in the /jira[ext]/setenv.sh to match the current node number

update jira service help desk in the "applications" section of jira

![[Pasted image 20240322154407.png]]
^ how you know the node is online

remember to restorecon on the second node as well

# IMPORTANT 
"when we're **upgrading** and copying to the 2nd node, it should only be the tar of the inst dir,  not the home dir.  When you're **creating** a new node for the cluster, you copy both"

# rando things
![[Pasted image 20240322154801.png]]