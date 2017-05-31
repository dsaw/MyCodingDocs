
#Try Git Tutorial

* _git init_ - initialises the git repository. A .git settings file is added to start **version control**

* _git status_ - checks the current status of the project. It will list the files not tracked, modified and to be committed

* _git add filename_ - adds the file to the staging area. This file will be tracked from now, in the git repo

* _git commit -m "commit message"_ - all the files/ changes in the staging area will be finalized for storing in the repository. 
	* A commit is like a snapshot of a repository at one point of time.

* _git add '*.txt' (wildcards)_ - A wildcard character * will match zero or more characters in the directory. All files with '.txt' as the suffix will be matched and added to repo in this case.

* _git log_ - It displays all the commits executed and their information(author, time, message). A summary can be displayed too with --summary

* _git remote add origin repo-url_ - Links a remote name 'origin' (or any specified name) to a remote repository.
	* A remote repository could be the user's git repository, a fork or a different server.
	* 'remote already exists' will be thrown up if the remote name already exists in local repo


	
