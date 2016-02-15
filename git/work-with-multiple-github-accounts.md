# Multiple github accounts

Often due to need, I need to use different github accounts on local and I use ssh for working with github. So, the per-user `SSH_CONFIG(5)` file is quite useful to achieve this. You can see the details of the client ssh configuration by typing `man 5 ssh_config` on your terminal.

Enough talking, lets see an example configuration so that you can manage multiple github accounts (or anything else that goes over ssh).

```
Host gh-orga
    User git
    HostName github.com
    IdentityFile ~/.ssh/orga

Host gh-orgb
    User git
    HostName github.com
    IdentityFile ~/.ssh/orgb

Host bb
    User git
    HostName bitbucket.org
    IdentityFile ~/.ssh/bitbucket
```

Now, I can just clone the private repositories via the appropriate host alias.

### Examples

`orga` private key's public key is added on my first github account and `orga` organization has a private repo `repox`.

```shell
$ git clone git@gh-orga:orga/repox.git
```

`orgb` private key's public key is added on my second github account and `orgb` has a private repo `repoy`.

```shell
$ git clone git@gh-orgb:orgb/repoy.git
```

Also, as you can see from the config example above, you can configure other git services, not just github. In fact, the `SSH_CONFIG(5)` is the OpenSSH client configuration file and is useful in several other cases for working with anything that uses ssh.
