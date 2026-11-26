---
type: reference
topic: tech
---

#git #theprimeagen #frontendmasters 

# notes 
* repo
	* a git tracked project
* commit 
	* a point in time representing the project in its entirety 
	* the sha that represents a commit, 40 a-f 0-9 characters, is calculated from the contents of change, author, time, and more 
* index 
	* i will use this term or staging area interchangeably 
* squash 
	* to take several commits and turn it into one commit
	* technically a squash would be taking N commits and turning it into N - 1 to 1 commit. but typically its N commits to 1 commit 
* work tree, working tree, main working tree 
	* this is your git repo. this is the set of files that represent your project. your working tree is setup by `git init` or `git clone` 
* git is an acyclic graph 
* in git, each commit is a node in the graph, and each pointer is the child to parent relationship 
* if you delete _untracked_ files they are lost forever. commit early, commit often, you can always change history to make it one commit (squashing) 
* `man git-<op>` for friendly manual 
* lots of people just know these commands: 
	* `push` 
	* `pull` 
	* `add` 
	* `commit` 
	* `status` 
* we will change some default states in this course 
	* `git config --get --global init.defaultBranch` 
	* `git config --global --unset init.defaultBranch` 
* git config your experience 
	* global config for every project 
	* specific, project-level config 
	* all git keys are `<section>.<key>` 
	* --global is for all projects 
	* user.name and user.email are the keys used in creating a commit tied to you 
	* to add a key value, execute `git config --add --global <key> <value>` 
	* view anything with `git config --get <key>` 
## create new repo 
* `git init` 
	* initialize git. adds .git folder to dir 
	* that's how you know it's a git repo 
	* to un-init a repo just delete the .git folder 
* prime thinks hooks are evil 
	* that's what your CI is for 
* 80% of git is 
	* `git add <path-to-file> | pattern` 
		* stages files 
	* `git commit -m <message>` 
		* takes staged files and commits them, producing a SHA (secure hashing algorithm) 
	* `git status` 
		* describes repo into like staged, tracked, untracked 
* first commit message should always be "batman" because he doesn't have any parents 
* should make a habit of using `git log` 
	* it has many options of making viewing of history a pleasant experience 
* you can specify the first 7 characters of a sha and git will identify what you're referring to 
	* `git log` is the simplest way to get a sha 
* the SHA is found in the `.git/objects/<first-2-sha-chars>` file 
* all of git state is stored in files. _everything_ 
* `git cat-file -p <some-sha>` 
	* echo out the contents of the sha. This can be a commit, tree, or blob 
* a tree is a dir that contains a set of files or more dirs
* a blob is a file
* `git cat-file -p <sha>` for my commit contained a sha for a tree 
	* the sha for that tree contained a blob
		* the sha for that blob contained file contents 
* **git does not store diffs, it stores the entirety of stuff** 
	* git stores pointers, not diffs 
* a single commit stores the entirety of the repo, not just diffs 
* `git config --list` will list out entire config 
	* `--get-regexp <regex>` also works, using pattern matching 
* git allows adding multiple keys (good for local and global settings) 
* `git config --get <key>.<value>` gets the latter of the two (or multiple) values 
* `--unset` is the opposite of `--add` 
* 

# random thoughts 