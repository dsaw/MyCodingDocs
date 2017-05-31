
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

* _git push -u origin master_ - Pushes the commits of the local repo to the remote repo denoted by name origin. the -u tells Git to remember the parameters.
	* Master will be the default local branch that will be pushed.

* _git pull origin master_ - Pulls down any changes to remote repo origin to local repo. The master branch will be pulled down. Opposite to git push.
	
* _git diff HEAD_ - Displays the differences between any two files, commits, index and commits or even the working directory and commit. HEAD denotes the last commit performed which is compared with the changes in the working tree

* _git diff --staged_ - Displays the differences between changes in the staging area and the commit specified. By default, assumes HEAD.

* _git reset files_ - Unstages the specified files. i.e: Removes them from changes to be committed. File is still present in directory though

* _git checkout -- filename_ - Updates the  corresponding files in working directory to the last commit(default) or index. Might remove the file too if no file in commit.
	* -- option specifies no option to be added after that point. it makes clear the type of checkout command.
	
* _git branch branchname_ - Creates a new branch. A branch is a separate copy of code that developers can work on for different features of the same project.

* _git checkout branchname_ - Switches to the specified branch.

* _git rm '*.txt'_ - Removes files from working directory and stages the removal for us.

* _git merge branch_ - Merges (copies) the changes of branch to the current  branch.
	* Merge conflicts can happen. Some files may have different changes in both the branches. Choose the changes you want to keep
	
* _git branch -d clean_up - Delete the branch after merging.
	* If branch is not merged and you have to delete it, add -d -f option.

