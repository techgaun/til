# Copy data from one measurement to another

I've not found a very reliable way except for [INTO clause](https://docs.influxdata.com/influxdb/v1.1//query_language/data_exploration/#the-into-clause) which is not really a export/import process but you read from one measurement and write to another. For our purpose, it works fine and there was no better way to do it efficiently (as of influxdb 1.1)

```shell
> SELECT energy INTO our_app."autogen".generation FROM src_measurement GROUP BY *
```

On our above example:

- `energy` is the field that we want to copy to another measurement
- `our_app` is the destination database
- `autogen` is the retention policy. If you don't specify, its supposed to use `DEFAULT` RP.
- `generation` is the destination measurement
- `src_measurement` is the source of data.
- `GROUP BY *` makes sure that all the tags are copied over.

## Notes

- Don't specify tag keys on SELECT fields part as it seems to prevent new writes later on.
- `GROUP BY tag_a, tag_b` would only copy `tag_a` and `tag_b` but I've not personally tested this.
- Often, this is easier than doing influxd backup and restore.
