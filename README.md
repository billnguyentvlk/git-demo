# git-demo
Simple repo to demo some git features


## Git rebase

**Rebase** means Reapply commits on top of another base tip

- Before:

```
          A---B---C---C1---C2 topic
         /
    D---E---F---G---G1---G2 master
```

- Action:

`git checkout topic`

`git rebase master`

- After: 

```
                          A'--B'--C'---C1'---C2' topic
                          /
    D---E---F---G---G1---G2 master
```