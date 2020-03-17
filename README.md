# git-demo
Simple repo to demo some git features
This repo is gonna be used to demo some git features


## Git rebase

**Rebase** means Reapply commits on top of another base tip

- Before:

```
          A---B---C topic
         /
    D---E---F---G master
```

- Action:

`git checkout topic`

`git rebase master`

- After: 

```
                  A'--B'--C' topic
                 /
    D---E---F---G master
```