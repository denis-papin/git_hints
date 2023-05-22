### == Get the branch cbl_xp_211101 from dev and create the same on ui124 ===

```
git fetch --all
git checkout -b cbl_xp_211101  # create the local branch
git push --set-upstream ui124 cbl_xp_211101  # send the content to a new remote branch
(optional) git branch --set-upstream-to=ui124/cbl_xp_211101  cbl_xp_211101 # define the new upstream for the local branch
git pull dev cbl_xp_211101
git push 
```

OR (better)

```
git fetch --all
git checkout --track dev/cbl_xp_211101 # pull the remote branch of dev and create the local branch that streams to dev
git push  --set-upstream ui124 cbl_xp_211101  # send the content to a brand new branch on ui124
git branch --set-upstream-to=ui124/cbl_xp_211101 cbl_xp_211101  # point the local branch to ui124 stream
```

### == Sync the forked branch ===

* (optional) make sure you have the right current branch  
```
git reset --hard ui124/november_2020
git reset --hard dev/may_2021
```

* (optional) create a new branch
```
git checkout -b may_2021 dev/may_2021
(better than git checkout -b may_2021)
git checkout --track dev/may_2021
```

* Check the source list
```
git remote -vv
```

* (optional) Add a new stream
```
git remote add dev https://github.deutsche-boerse.de/dev/cs.xact
```

* Check the source list
```
git remote -vv
```

* Pull the change from the stream
```
git fetch dev
```
* stash your changes 
```
git stash
```
* Merge the stream branch 
```
git pull dev may_2021
(git merge dev/may_2021)
git push
(git push --set-upstream ui124 may_2021)
```

##### From IntelliJ
Go to "Git/Uncommit changes/Unstash changes"  and handle the conflict through the GUI

### ==  Switch to a new branch ===

```
git checkout ocapi_p1
```

OR

```
git fetch
git checkout --track dev/ocapi_p1
```


### Shortcuts
```
alias gs='git status'
alias gb='git branch -vv'
alias gl='git log --graph'
alias gr='git remote -vv'
```

### Useful git commands

<b>Classic pull </b>
```
git pull dev november_2020
```
<b>Add a stream </b>
```
git remote add <stream> https://github.com/dev/cs.xact.git
```
<b>Change branch</b>

1. When you are not on a branch but on the right remote stream
```
	git checkout <branch>  (if the local branch exists)
	git checkout -b <branch> (if the local branch must be created)
```

Note :  If you checkout both the orgin stream and the fork, the branch names can conflict locally. 
		Usually, we don't checkout the origin stream

2. When the remote upstream is not defined for the current branch
```
	git push --set-upstream <stream> <branch>
	git push --set-upstream ui124 phase1
	
	git branch --set-upstream-to=<remote>/<branch> <local-branch>
	git branch --set-upstream-to=ui124/may_2021  2021
```
<b>Ignore a file</b>
```
git update-index --assume-unchanged jboss7xx/configuration/standalone.xml
```
<b>Reset a local repo from the stream</b>
```
git reset --hard ui124/november_2020
```
<b>Rename a stream</b>
```
git remote rename origin dev 
```
<b>List differences of "staged" files</b>
```
git diff --staged
```
	
<b>Stage and commit all the files</b>
```
git commit -a -m 'added new benchmarks' 
```
	
<b>Remove file</b>
```
git rm LISEZMOI : delete a file from git and from the workspace
git rm -f LISEZMOI : delete a file from git even after the staging , and delete the file from the workspace
git rm --cached LISEZMOI : delete a file from git even after the staging was done, but leave it in the workspace
```
	
<b>Modify the last commit </b>
```
git commit --amend  : remplace le dernier commit; ajoute les nouveaux "staged files" et change le message.
```
	
<b>Reset a file from the stream</b>
```
git reset HEAD CONTRIBUTING.md
```

<b>Rename a local branch</b>
```
git branch -m <new_name>
```
	
<b>Get the commit number at a specific date </b>
```
git rev-list -n 1 --before="2021-08-18 12:00" dev/cbl_xp_211101
```

<b>The Travolta Dance</d>

We suppose we have pushed commits on the `feature` branch.
`develop` is our main branch.
We want to get clean commit history of our `feature` branch to be merged in `develop`

```
git checkout develop
(git reset --hard origin/develop)
git branch -d feature
git checkout -b feature
pull origin feature --no-commit
#if there isn't any conflict with the pull, there is no need to commit later on
# ... modify other files if needed here
# ... then commit if needed
git commit -m"last commit from feature and conflicts resolution"
git push -u origin feature
```
 or better 
 
 ```
# ATTENTION : vérifier sur Gitlab que le dernier commit de feature a été poussé !!!!
# A partir de la branche `feature` :
feature$ git reset --hard origin/develop
feature$ pull origin feature --no-commit
#if there isn't any conflict with the pull, there is no need to commit later on
# ... modify other files if needed here
# ... then commit if needed
feature$ git commit -m"last commit from feature and conflicts resolution"
feature$ git push
```
