# Common Issues & Fixes


## 🔧 thinkfan.service inactive after reboot

- **Likely systemd service `systemd.service` is not enabled:**

  ```bash
  sudo systemctl enable thinkfan
  ```


## 🌀 Fan not running at expected speeds

- Check if fan control is enabled:

  ```bash
  test -r /proc/acpi/ibm/fan && echo "Fan control enabled" || echo "Fan control not enabled"
  ```

- Alternatively:

  ```bash
  cat /sys/module/thinkpad_acpi/parameters/fan_control
  # Output should be 'Y' for enabled and 'N' for not enabled
  ```

- Validate thinkpad_acpi is loaded:

  ```bash
  lsmod | grep thinkpad
  ```

## 🔐 Permissions Errors

- Always run fan commands as sudo

- Ensure user is in `video` and `lp` groups if required
