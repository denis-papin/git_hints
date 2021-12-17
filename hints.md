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

### Shortcuts


git status

gl git log  -6 --graph

gb git branch -vv

gr git remote -vv

### Classic pull 

git pull dev november_2020
