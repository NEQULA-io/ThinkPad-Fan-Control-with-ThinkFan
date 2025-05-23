# Common Issues & Fixes


## 🔧 thinkfan.service inactive after reboot

- **Likely systemd service is not enabled:**

  ```bash
  sudo systemctl enable thinkfan
  ```


## 🌀 Fan not running at expected speeds

- Check if fan control is enabled:

  ```bash
  cat /proc/acpi/ibm/fan
  ```

- Validate thinkpad_acpi is loaded:

  ```bash
  lsmod | grep thinkpad
  ```

## 🔐 Permissions Errors

- Always run fan commands as sudo

- Ensure user is in video and lp groups if required
