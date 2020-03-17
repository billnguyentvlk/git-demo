# git-demo
Simple repo to demo some git features


## Git rebase

**Rebase** means Reapply commits on top of another base tip

- BEFORE:

```
          A---B---C---C1---C2 topic
         /
    D---E---F---G---G1---G2 master
```

- ACTION:

`git checkout topic`

`git rebase master`

- AFTER: 

```
                          A'--B'--C'---C1'---C2' topic
                          /
    D---E---F---G---G1---G2 master
```
