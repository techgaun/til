## OpenSSL and SSL Cert tips

### check the creation and expiry date

```shell
echo | openssl s_client -connect example.com:8443 2>/dev/null | openssl x509 -noout -dates
```

Output looks something like below:

```shell
notBefore=Mar 22 21:53:00 2017 GMT
notAfter=Jun 20 21:53:00 2017 GMT
```
