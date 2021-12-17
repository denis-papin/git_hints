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

##### (optional) make sure you have the right current branch  
git reset --hard ui124/november_2020

git reset --hard dev/may_2021

##### (optional) create a new branch
git checkout --track dev/may_2021
(better than git checkout -b may_2021)

##### Check the source list
git remote -vv

##### (optional) Add a new stream
git remote add dev https://github.deutsche-boerse.de/dev/cs.xact

##### Check the source list
git remote -vv

##### Pull the change from the stream

git fetch dev

##### stash your changes 
git stash

##### Merger the stream branch 
git merge dev/may_2021  
git push
#git push --set-upstream ui124 may_2021

##### From IntelliJ
Go to "Git/Uncommit changes/Unstash changes"  and handle the conflict through the GUI

//////////

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

alias gs='git status'
alias gb='git branch -vv'
alias gl='git log --graph'
alias gr='git remote -vv'

### Classic pull 

git pull dev november_2020


