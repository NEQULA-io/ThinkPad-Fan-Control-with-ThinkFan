# 🔴 🅣 ThinkPad Fan Control with ThinkFan

A clean and comprehensive walkthrough for configuring **`ThinkFan`** on supported ThinkPad models.

Control your **ThinkPad** fan manually and dynamically. This `ThinkFan` based setup gives finer thermal management, quieter operation, and greater control. This project documents everything from setup to advanced tweaks.


## 💡 Features

- 🧊 Configurable fan levels based on temperature thresholds

- 🔁 Automatic startup at boot

- 💾 Persistent settings across reboots

- 🛡️ Safe limits to avoid hardware damage

- 📈 Real-time temperature and fan monitoring


## 🚀 Quick Start

1. **Install `ThinkFan` & sensors:**

    ```bash
    sudo apt update
    sudo apt install thinkfan lm-sensors
    sudo sensors-detect
    ```

2. **Enable fan control kernel module:**

    ```bash
    echo options thinkpad_acpi fan_control=1 | sudo tee /etc/modprobe.d/thinkfan.conf
    ```

3. **Make persistent:**

    ```bash
    echo "thinkpad_acpi" | sudo tee -a /etc/initramfs-tools/modules
    sudo update-initramfs -u
    sudo reboot
    ```

4. **Configure `ThinkFan`:**

    ```bash
    sudo cp config/thinkfan.conf.current /etc/thinkfan.conf
    ```

5. **Enable and Re-start `ThinkFan`:**

    ```bash
    sudo systemctl enable thinkfan
    sudo systemctl restart thinkfan
    ```

6. **Start `ThinkFan` (Optional):**

    ```bash
    sudo systemctl start thinkfan
    ```

8. **Check status:**

    ```bash
    sudo systemctl status thinkfan
    ```
9. **Monitor `ThinkFan` in real-time:**

   ```bash
    watch -n 1 cat /proc/acpi/ibm/fan
    ```


For full installation help, see [Autostart](Docs/autostart.md) and [Persistent Control](Docs/persistent-control.md).

## 🔧 Pre-set `config/thinkfan.conf`

Original configuration showing basic syntax, sensor references, and safe fallback values. Useful for reverse engineering or resetting.

## 🔧 Custom `config/thinkfan.conf`

Custom config tuned for modern ThinkPads:
(Note: You can simply copy-paste the contents.)

```bash
sensors:
  - hwmon: /sys/class/hwmon
    name: coretemp
    indices: [1, 2, 3, 4, 5, 6]  # CPU cores
  - hwmon: /sys/class/hwmon
    name: thinkpad
    indices: [1, 2]  # CPU and GPU

fans:
  - tpacpi: /proc/acpi/ibm/fan

levels:
  - [0, 0, 45]              # Fan off below 45 °C
  - ["level 1", 42, 50]     # Gentle spin
  - ["level 3", 48, 60]     # Moderate cooling
  - ["level 5", 55, 70]     # High cooling
  - ["level auto", 68, 78]  # BIOS-assisted
  - ["level 7", 75, 255]    # Max speed
```

- 🔍 Uses fan levels 0 to 7 (avoids disengaged)

- 🌡️ Relies on core temp sensors for thermal management

- 🎚️ Ensure sensors exist in sensors output

## 🤝 Contribution

We welcome community pull requests with:

- Configs for new ThinkPad models

- Custom profiles for low-noise or aggressive cooling

- Safety improvements and documentation updates

## 🎛 **Built in Slience for Performance and full control.**
