## Clone From Remote with Expired SSL Cert

You might see something like `server certificate verification failed.` when you try to clone from remote with ssl cert
expired or invalid. Quick way to fix this is:

```shell
GIT_SSL_NO_VERIFY=1 git clone <remote-url>
```
