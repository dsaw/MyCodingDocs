
## Try Git Tutorial

* `git init` - initialises the git repository. A .git settings file is added to start **version control**

* `git status` - checks the current status of the project. It will list the files not tracked, modified and to be committed

* `git add filename` - adds the file to the staging area. This file will be tracked from now, in the git repo

* `git commit -m "commit message"` - all the files/ changes in the staging area will be finalized for storing in the repository. 
	* A commit is like a snapshot of a repository at one point of time.

* `git add '*.txt' (wildcards)` - A wildcard character * will match zero or more characters in the directory. All files with '.txt' as the suffix will be matched and added to repo in this case.

* `git log` - It displays all the commits executed and their information(author, time, message). 
	* A summary can be displayed too with `--summary`
	* Other useful flags : `--oneline`, `--graph`, `--patch`.

* `git remote add origin repo-url` - Links a remote name 'origin' (or any specified name) to a remote repository.
	* A remote repository could be the user's git repository, a fork or a different server.
	* 'remote already exists' will be thrown up if the remote name already exists in local repo

* `git push -u origin master` - Pushes the commits of the local repo to the remote repo denoted by name origin. the -u tells Git to remember the parameters.
	* Master will be the default local branch that will be pushed.

* `git pull origin master` - Pulls down any changes from remote repo origin to local repo. The master branch will be pulled down and merged in to the current working branch. Opposite to git push. It is a combination of fetch and merge.
	
* `git diff HEAD` - Displays the differences between any two files, commits, index and commits or even the working directory and commit.
					HEAD denotes the last commit performed which is compared with the changes in the working tree
	* `git diff --staged` - Displays the differences between changes in the staging area and the commit specified. By default, assumes HEAD.
	* `--diff-version=ACDM` - Displays only the files that were added, copied, deleted and modified respectively.


* `git reset files` - Unstages the specified files. i.e: Removes them from changes to be committed. File is still present in directory though. --soft, --hard, --mixed flags do not have any effect in the file level version.

* `git checkout -- filename` - Updates the  corresponding files in working directory to the last commit(default) or index. Might remove the file too if no file in commit.
	* -- option specifies no option to be added after that point. it makes clear the type of checkout command.
	* `git checkout --ours/--theirs -- filepaths` - When faced with merge conflicts, there will be unmerged entries. Specify `ours` to choose the current branch's version or `theirs` to choose the other branch's one.
	
* `git branch branchname` - Creates a new branch. A branch is a separate copy of code that developers can work on for different features of the same project.

* `git checkout branchname` - Switches to the specified branch.

* `git rm '*.txt'` - Removes files from working directory and stages the removal for us.

* `git merge branch` - Merges (copies) the changes of branch to the current  branch.
	* Merge conflicts can happen. Some files may have different changes in both the branches. You will have to choose the changes you want to keep by using merge tools.
	* If you don't want to resolve the conflicts yet, run `git merge --abort` which will return the repo as it was before.
	
* `git rebase anotherbranch` - Rebases the commits of the current branch from the common ancestor onto the  tip of the target branch. 
	* It is very similar to a merge, except the history of the repo is completely changed. Now only a linear series of commits are apparent.
	* Conflicts may have to be resolved just like in merge.
	* Interactive rebase with an `-i` flag supports options to modify the series of commits. You can reorder, squash them together, split into multiple commits, change individual commits and more. The rebase should be done on an ancestor of HEAD i.e. `git rebase -i HEAD~3`
	
* `git branch -d clean-up` - Delete the branch after merging.
	* If branch is not merged and you have to delete it, add -d -f option.

* `git push remoteref branch`- Push all the changes to branch of remote repository.

* `git fetch remoteref branch` - Fetches down any changes from remote repo to local repo. It will merge them like *git pull*, giving a chance to review it. Remote branches are updated.

* `git revert commit` - Generates a new commit that undos the changes performed with respect to the specified commit. It will maintain the commit history unlike reset which will discard the commits after the specified commit **resetted** back to.

* `git cherry-pick commit-hash` - Chooses commits from potentially different branches and applies them to HEAD. Multiple commits can be picked too.
	* If you want to edit the changes first, pass `--no-commit` which will stage the changes introduced by commits.
	
