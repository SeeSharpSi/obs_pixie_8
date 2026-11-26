---
type: reference
topic: tech
---

#git #theprimeagen #frontendmasters 

# Notes 
* Repo
	* A git tracked project
* Commit 
	* A point in time representing the project in its entirety 
	* The sha that represents a commit, 40 a-f 0-9 characters, is calculated from the contents of change, author, time, and more 
* Index 
	* I will use this term or staging area interchangeably 
* Squash 
	* To take several commits and turn it into one commit
	* Technically a squash would be taking N commits and turning it into N - 1 to 1 commit. but typically its N commits to 1 commit 
* Work tree, working tree, main working tree 
	* This is your git repo. This is the set of files that represent your project. Your working tree is setup by `git init` or `git clone` 
* Git is an acyclic graph 
* In git, each commit is a node in the graph, and each pointer is the child to parent relationship 
* If you delete _untracked_ files they are lost forever. Commit early, commit often, you can always change history to make it one commit (squashing) 
* `man git-<op>` for friendly manual 
* Lots of people just know these commands: 
	* `push` 
	* `pull` 
	* `add` 
	* `commit` 
	* `status` 
* We will change some default states in this course 
	* `git config --get --global init.defaultBranch` 
	* `git config --global --unset init.defaultBranch` 
* Git config your experience 
	* Global config for every project 
	* Specific, project-level config 
	* All git keys are `<section>.<key>` 
	* --global is for all projects 
	* User.name and user.email are the keys used in creating a commit tied to you 
	* To add a key value, execute `git config --add --global <key> <value>` 
	* View anything with `git config --get <key>` 
## Create new repo 
* `git init` 
	* Initialize git. Adds .git folder to dir 
	* That's how you know it's a git repo 
	* To un-init a repo just delete the .git folder 
* Prime thinks hooks are evil 
	* That's what your CI is for 
* 80% of git is 
	* `git add <path-to-file> | pattern` 
		* Stages files 
	* `git commit -m <message>` 
		* Takes staged files and commits them, producing a SHA (secure hashing algorithm) 
	* `git status` 
		* Describes repo into like staged, tracked, untracked 
* First commit message should always be "batman" because he doesn't have any parents 
* Should make a habit of using `git log` 
	* It has many options of making viewing of history a pleasant experience 
* You can specify the first 7 characters of a sha and git will identify what you're referring to 
	* `git log` is the simplest way to get a sha 
* The SHA is found in the `.git/objects/<first-2-sha-chars>` file 
* All of git state is stored in files. _everything_ 
* `git cat-file -p <some-sha>` 
	* Echo out the contents of the sha. This can be a commit, tree, or blob 
* A tree is a dir that contains a set of files or more dirs
* A blob is a file
* `git cat-file -p <sha>` for my commit contained a sha for a tree 
	* The sha for that tree contained a blob
		* The sha for that blob contained file contents 
* **Git does not store diffs, it stores the entirety of stuff** 
	* Git stores pointers, not diffs 
* A single commit stores the entirety of the repo, not just diffs 
* `git config --list` will list out entire config 
	* `--get-regexp <regex>` also works, using pattern matching 
* Git allows adding multiple keys (good for local and global settings) 
* `git config --get <key>.<value>` gets the latter of the two (or multiple) values 
* `--unset` is the opposite of `--add` 

# random thoughts 