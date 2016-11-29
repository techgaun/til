# Get Latest Tag

You can use the following git command to get the most recent tag in git repos.
This is what I prefer so that I can checkout to the most recent tag of the repos
I clone so that I can stay on most stable version (as long as repo maintainers use tag for releases)

```shell
git describe --tags $(git rev-list --tags --max-count=1)
```

You can also wrap that to perform a checkout:

```shell
git checkout $(git describe --tags $(git rev-list --tags --max-count=1))
```
