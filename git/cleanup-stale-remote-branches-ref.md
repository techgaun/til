# Remove all stale tracking branches removed from remote repo

Your `git branch -a` starts to grow bigger and bigger as you continue to work on git.

Example:

```shell
$ git branch -a
  aggregation
* master
remotes/origin/HEAD -> origin/master
remotes/origin/featureX
remotes/origin/featureY
remotes/origin/featureN
remotes/origin/master
```

The above can grow pretty quickly. The way to get rid of them is by running the following command:

```shell
git remote prune origin # git remote prune <remote_name>
```

You might want to see what would be pruned before actually pruning by adding an argument `--dry-run`.

```shell
git remote prune origin --dry-run
```
