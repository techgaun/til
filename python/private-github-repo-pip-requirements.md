## Private Github Repo with Pip

With pip, you can specify github URLs and to include private repos, its similar as what we did for
[elixir](../elixir/priv-ghrepo-deps.md)

Just add the line in your requirements file as below:

```
git+https://{personal_access_token}:x-oauth-basic@github.com/{git_username}/{project}.git@branch#egg=project-xyz
```
