 ## Initialize a local git repository: git init
mkdir frizz
cd frizz
git init .

# Initialize a local git repository: git init --bare
mkdir sparkle
cd sparkle
git init --bare .
# using git init --bare, all the information is in the root directory.
# There is no .git directory.
# This does not create a work directory. You can use it only to push and pull. You can not write code here.

## Setting up git configuration
git config --global user.name "mickey_mouse"
git config --global user.email "mickymouse@email.com"
git config --list # show you your configurations

# Remove and Delete properties from git config
git config --global --unset user.email # --global is scope and --user.email is what property we want to remove.

# But if you stored more than one user email, git assked you to remove all or none.
git config --global --unset-all user.email

# Change the text editor
git config --global core.editor "nano"

git config --get user.email

## git add and git commit
git add file_name  # add file into staging area
git add .     # add all filess into staging area

git commit -m "commit message" 

git add . && git commit -m "commit message" # add and ccommit in one go

# revert/undo a git commit
git revert <commit hash number> # It will revert/remove all the files of that particular commit. Rest is untouched

# git reset
git reset --hard <commit hash number> # It will set back to that particular commit, rest of all (commit/files) will be removed.

git status # check the tracked/untracked files

git ls-files # check tracked/staged files only

# Remove add file(s) before commit
git reset file_name

## Add remote repository to local
git remote add origin <remote_repo_link>

git remote 

git remote -v #check remote repos connected your local 

## git push (send changes from local to remote repo)
git push -u origin main # -u is upstream that means if we are working on same project or same repo and we don't need to specify origin main again aand again. We can simply use git push

## push an empty directory
# create .gitkeep file into the empty folder. Then staged, commit and push it.

# push a local git branch to a remote github
git push --set-upstream origin <new branch name> #once
# switch to branch and simply 
git push origin # changes sent to remote branch

## git pull (fetch changes from remote repo to local)
git pull origin main

## git clone
# If clone a repo from other profile(you aare not a member of that gropu), we can't push changes to main. Use fork instead clone. 
git clone <link>

# clone into specific directory
git clone <link> directory_name

# clone a specific branch only
git clone --single-branch --branch [name of branch] <link> 

## git fork
# fork any repository and clone itno your local system.
# fork via terminal
gh repo fork <link> --clone

## git log
git log  # gives commit history
git reflog # about local commit history. It's only paart of your local working directory.
git log --oneline # shows commit history in one line
git log --oneline --stat # shows modificaations/changes made
git log --pretty=oneline
git log --pretty=short
git log --pretty=short --oneline
git log --pretty=medium
git log --pretty=full
git log --pretty=fuller
git log --pretty=reference
git log --pretty=email
git log --pretty=raw
git log --pretty=%C(yellow) Hash: %h %C(blue) Date: %ad %C(red) Message: %s " --date=human"
git log --pretty=%C(green) %s %C(white) is %cn's comit %C (yellow) on %cd" --date=short

git log --graph
git log --graph --oneline

## git clean
# It does not clean ignore files(gitignore)
git clean -n # remove all the untracked unstaged files
git clean -n -x -d  # forcefully delete untracked ignore files or directory
git clean --force -x -d 

## git branch
git branch <branch name> # create a new branch
git branch # know which branch you are currently in
git branch -a
git switch -c <new branch> # craete and switch into a new branch
git checkout -b <new branch name> # create a new branch + switch to it
git branch -M <old branch name> <new name> # rename branch
git checkout <branch name> # navigate/move to a particular branch
git tag 
git branch <branch name> <tag name>
git clean -f

# delete local git branch(es)
# switch to main/other branch and then type
git branch -d <branch name> # delete branch

# delete remote branch
git push origin --delete <remote branch name>
# and then delete that branch locally too

# merge git branch to main branch
git merge <branch name>

# resolve merge conflict
# open and correct the conflict on the file (manually) you want to meerge on a branch.
git add .
git commit -m "resolve conflict"
# This change only haappen to the branch you want to merge the file.

# canceel git merge process
git merge --abort

git reset --hard
