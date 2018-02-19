## Copy CSV from remote server to local filesystem on Postgres

I knew of `\copy` meta-command with postgres but had never used it before.
When I had to copy CSV from remote server, I initially thought, the `\copy`
is just gonna work on the server side so I didn't really pursue at first.
But, in fact, it is supposed to run on client side unlike the `COPY` command itself.

Examples:

```
psql> \copy (select name as unit_name from units where property_id = 10 and active = true) TO '/tmp/units.csv' With CSV Header

psql> \copy (select name as unit_name from units where property_id = 10 and active = true) TO '/tmp/units.csv' With CSV Header Delimiter '|'
```
