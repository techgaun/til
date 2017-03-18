# Private Github Repo as Package dependency

For public repos, you can just do something like below in your `mix.exs`:

```
defp deps do
  [{:awesome_pkg, github: "techgaun/awesome_pkg"}]
end
```

For private repos, you can do it one of two ways.

#### Add ssh key to the user that has access to repo and specify git url with ssh

```
defp deps do
  [{:awesome_pkg, git: "git@github.com:techgaun/awesome_pkg.git"}]
end
```

However this does not always cater your need. For example, if your deployment service requires it to pull the private repo but you can not get ssh pub key of that service. you need something else.

#### Use personal access token

Get yourself (or for dedicated machine user) a personal access token from [github settings page](https://github.com/settings/tokens). I personally like to keep it separate and also just give repo:read for the token.

```
defp deps do
  [{:awesome_pkg, git: "https://<PUT_YOUR_TOKEN>@github.com/techgaun/awesome_pkg.git"}]
end
```
