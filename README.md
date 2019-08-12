# git

Helpful tips and files for git

## Git Basics

The first command used to initialize the project, executed in the root working directory of the
project:
```bash
  $ git init
```
 
How to add files to the stage:
```bash
  $ git add .
  # or
  $ git add <individual file>
```
 
This commits your changes, commit messages should be present tense:
```bash
  $ git commit -m "add javascript file"
```

Gives a snapshot of the stage:
```bash
  $ git status
```

Gives a record of your commits:
```bash
  $ git log
```

## Remote Repositories

This is how you check to see what remote repositories are associated with your local repo:
```bash
  $ git remote -v
```

This is how to connect the working directory on your machine with the repository on github, a
one-time setup command:
```bash
  $ git remote add origin https://github.com/sfdeloach/c-prog-solutions.git
```

This will push all staged files to the repository:
```bash
  $ git push origin master
```

This will pull all files from the repository to your working local directory:
```bash
  $ git pull origin master
```

Checkout a previous commit or a branch from your repository:
```bash
  $ git checkout <<hash from git log>> // to revert to a previous commit
  $ git checkout master                // for the head to resume on the master commit
```

This is how to remove a directory (named node-modules) from your git repo...node-modules is a good
directory to not include in your repo due its size and availability to download via npm (also, it
should be listed in your `.gitignore` as well):
```bash
  $ git rm -r --cached node-modules
  $ git commit -m 'Remove the now ignored directory node_modules'
  $ git push origin master
```

## Git Branches

List all of the branches in your repo. Add a `<branch>` argument to create a new branch with the
name `<branch>`:
```bash
  $ git branch
  $ git branch <branch>
```

Create and checkout a new branch named `<branch>`. Drop the `-b` flag to checkout an existing
branch:
```bash
  $ git checkout -b <branch>
```
    
Merge `<branch>` into the current branch:
```bash
  $ git merge <branch>
```

## Rename a Local Branch and a Remote Branch

Rename the branch locally:
```bash
  $ git branch -m <old branch> <new branch>
```
    
Delete the old branch from your remote repository:
```bash
  $ git push origin :<old branch>  // <-- note the colon ':' preceeding the name of the old branch
```
    
Push the new branch, set the local branch to track the new remote branch:
```bash
  $ git push --set-upstream origin <new branch>
```

## Fetch a remote branch and set as a local branch

First fetch the branch from your repository:
```bash
  $ git fetch origin <remote branch>
```
    
Then set your local branch to track changes made on the remote branch:
```bash
  $ git checkout --track origin/<remote branch>
```
