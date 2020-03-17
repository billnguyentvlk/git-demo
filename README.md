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

## Rebase -onto

If the upstream branch already contains a change you have made (e.g., because you mailed a patch which was applied upstream), then that commit will be skipped. For example, running `git rebase master` on the following history (in which `A'` and `A` introduce the same set of changes, but have different committer information):

```
          A---B---C topic
         /
    D---E---A'---F master
```


will result in:

```
                   B'---C' topic
                  /
    D---E---A'---F master
```

Here is how you would transplant a topic branch based on one branch to another, to pretend that you forked the topic branch from the latter branch, using `rebase --onto.`

First let’s assume your topic is based on branch next. For example, a feature developed in topic depends on some functionality which is found in next.

```
    o---o---o---o---o  master
         \
          o---o---o---o---o  next
                           \
                            o---o---o  topic
```
We want to make topic forked from branch master; for example, because the functionality on which topic depends was merged into the more stable master branch. We want our tree to look like this:

```
    o---o---o---o---o  master
        |            \
        |             o'--o'--o'  topic
         \
          o---o---o---o---o  next
```

We can get this using the following command:

`git rebase --onto master next topic`

Another example of --onto option is to rebase part of a branch. If we have the following situation:
```
                            H---I---J topicB
                           /
                  E---F---G  topicA
                 /
    A---B---C---D  master
```

then the command

`git rebase --onto master topicA topicB`

would result in:

```
                 H'--I'--J'  topicB
                /
                | E---F---G  topicA
                |/
    A---B---C---D  master
```

This is useful when topicB does not depend on topicA.