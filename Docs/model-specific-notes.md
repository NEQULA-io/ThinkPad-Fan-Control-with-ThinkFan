# ThinkPad Model Differences

Some ThinkPad models expose fan sensors or thermal zones under different labels. Always check using:

```bash
sensors
ls /sys/class/hwmon/*/name
```

For example:

- X1 Carbon Gen 9: sensor may appear under `nvme`, not `coretemp`

- T14 AMD: needs manual override of `hwmon` index in `/etc/thinkfan.conf`
