## Serial Device Sniffing

- Install [interceptty](freecode.com/projects/interceptty) ([Here's a copy](https://github.com/techgaun/dumpster/tree/master/zwave/openZSniffer))
- Start sniffing: `interceptty -s 'ispeed 115200 ospeed 115200' /dev/ttyACM0 /tmp/ttyACM0`
- Add an [alias](https://github.com/techgaun/dotfiles/blob/1c0244cc326311d4e2270c49e974f3308b1a4a09/.bash_aliases#L30)
- Sample output

```
0x01,  0x07,  0x00,  0x13,  0x01,  0x00,  0x00,  0x02,  0xe8,  

|Direction|Hex|Dec|Description|
|---|---|---|---|
|>| 0x01|1|__Header=SOC__|
|>| 0x07|7|Length=7 |
|>| 0x00|0|Type=REQUEST |
|>| 0x13|19|function=SendData |
|>| 0x01|1| |
|>| 0x00|0| |
|>| 0x00|0| |
|>| 0x02|2| |
|>| 0xe8|232|Checksum |
```
