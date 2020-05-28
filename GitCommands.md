# GitCommands
A place to store helpful Git commands

## Remove a file from a repo ##

  ```bash
  git rm --cached <filename>
  git commit -m "Deleting file"
  ```
  
  source: https://stackoverflow.com/questions/11628418/git-cant-ignore-suo-file/11629271
  
  ## Force pull to overwrite local files ##
  
  ```bash
  git fetch --all
  ```
  
  THEN
  
  ```bash
  git reset --hard origin/master
  ```
  OR
  ```bash
  git reset --hard origin/<branch_name>
  ```
  
  EXPLANTATION
  git fetch downloads the latest from remote without tyring to merge or rebase anything. 
  
  Then the git reset resets the master branch to what you just fetched. The --hard optoin changes all the files in your 
  working tree to match the files in origin/master.
  
  ### Maintain current local commits ###
  [*]: It's worth noting that it is possible to maintain current local commits by creating a branch from master before resetting:
  ```bash
  git checkout master
	git branch new-branch-to-save-current-commits
	git fetch --all
	git reset --hard origin/master
  ```

  After this, all of the old commits will be kept in new-branch-to-save-current-commits.
  Uncommitted changes

  Uncommitted changes, however (even staged), will be lost. Make sure to stash and commit anything you need. For that you can 
  run the following:

  ```bash
	git stash
  ```
  And then to reapply these uncommitted changes:
  ```bash
	git stash pop
  ```
  
  source: https://stackoverflow.com/questions/1125968/how-do-i-force-git-pull-to-overwrite-local-files  
  
