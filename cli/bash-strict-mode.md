## Bash Strict Mode

The original article is [here](http://redsymbol.net/articles/unofficial-bash-strict-mode/) and I agree with author.

```shell
#!/bin/bash
set -euo pipefail
IFS=$'\n\t'
```
