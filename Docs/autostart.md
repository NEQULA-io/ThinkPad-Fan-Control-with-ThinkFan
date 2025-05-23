Make ThinkFan start automatically on boot

1. **Enable service:**

    ```bash
    sudo systemctl enable thinkfan
    ```

3. Confirm **fan_control=1** is applied via **`/etc/modprobe.d/thinkfan.conf`**

3. **Check logs:**

    ```bash
    journalctl -u thinkfan
    ```

4. **Optional:**

    Add delays to startup sequence via **systemd** if **ThinkFan** loads too early
