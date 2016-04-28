# Command Line presentations with markdown syntax using mdp
* **markdown**

```shell
apt-get install markdown lynx
markdown <markdown_file> | lynx -stdin
```

* **pandoc**

```shell
apt-get install pandoc lynx
pandoc <markdown_file> -f markdown -t html | lynx -stdin
```

You might want to create a bash function since you will use this frequently

* **using markdown**
```shell
function mdview {
pandoc "$1" -f markdown -t html | lynx -stdin
}
```

* **using pandoc**

```shell
function mdview {
markdown "$1" | lynx -stdin
}
```
