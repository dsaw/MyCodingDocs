## Try Git tutorial

- _What is git_
  - Git is a distributed version control system. It allows group of people to work on the same files.
  - Unlike other VCS's it stores the snapshot of the files instead of the files themselves.
 
- _Initialise a repository_
  - Call `git init` in the directory to be initialised.
  - A hidden directory .git is created where all the snapshots will be saved.
  
- _Status of repository_
  - To see the current state of the project, run `git status`
  - It displays the files being tracked, modified and ready to be committed
  - Use it often
  
  
- _Git workflow_
  - The repository_ contains the files and folders that are worked upon called the *working directory*
  - The changes that are prepared to be committed are in the *staging area* aka index
  - Changes represent the snapshot that will be committed. 