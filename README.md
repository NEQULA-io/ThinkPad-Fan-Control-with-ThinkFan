```
████████╗██╗  ██╗██╗███╗   ██╗██╗  ██╗██████╗  █████╗ ██████╗     ███████╗ █████╗ ███╗   ██╗
╚══██╔══╝██║  ██║██║████╗  ██║██║ ██╔╝██╔══██╗██╔══██╗██╔══██╗    ██╔════╝██╔══██╗████╗  ██║
   ██║   ███████║██║██╔██╗ ██║█████╔╝ ██████╔╝███████║██║  ██║    █████╗  ███████║██╔██╗ ██║
   ██║   ██╔══██║██║██║╚██╗██║██╔═██╗ ██╔═══╝ ██╔══██║██║  ██║    ██╔══╝  ██╔══██║██║╚██╗██║
   ██║   ██║  ██║██║██║ ╚████║██║  ██╗██║     ██║  ██║██████╔╝    ██║     ██║  ██║██║ ╚████║
   ╚═╝   ╚═╝  ╚═╝╚═╝╚═╝  ╚═══╝╚═╝  ╚═╝╚═╝     ╚═╝  ╚═╝╚═════╝     ╚═╝     ╚═╝  ╚═╝╚═╝  ╚═══╝
                                                                                            
 ██████╗ ██████╗ ███╗   ██╗████████╗██████╗  ██████╗ ██╗         ██╗    ██╗██╗████████╗██╗  ██╗
██╔════╝██╔═══██╗████╗  ██║╚══██╔══╝██╔══██╗██╔═══██╗██║         ██║    ██║██║╚══██╔══╝██║  ██║
██║     ██║   ██║██╔██╗ ██║   ██║   ██████╔╝██║   ██║██║         ██║ █╗ ██║██║   ██║   ███████║
██║     ██║   ██║██║╚██╗██║   ██║   ██╔══██╗██║   ██║██║         ██║███╗██║██║   ██║   ██╔══██║
╚██████╗╚██████╔╝██║ ╚████║   ██║   ██║  ██║╚██████╔╝███████╗    ╚███╔███╔╝██║   ██║   ██║  ██║
 ╚═════╝ ╚═════╝ ╚═╝  ╚═══╝   ╚═╝   ╚═╝  ╚═╝ ╚═════╝ ╚══════╝     ╚══╝╚══╝ ╚═╝   ╚═╝   ╚═╝  ╚═╝
                                                                                               
████████╗██╗  ██╗██╗███╗   ██╗██╗  ██╗███████╗ █████╗ ███╗   ██╗
╚══██╔══╝██║  ██║██║████╗  ██║██║ ██╔╝██╔════╝██╔══██╗████╗  ██║
   ██║   ███████║██║██╔██╗ ██║█████╔╝ █████╗  ███████║██╔██╗ ██║
   ██║   ██╔══██║██║██║╚██╗██║██╔═██╗ ██╔══╝  ██╔══██║██║╚██╗██║
   ██║   ██║  ██║██║██║ ╚████║██║  ██╗██║     ██║  ██║██║ ╚████║
   ╚═╝   ╚═╝  ╚═╝╚═╝╚═╝  ╚═══╝╚═╝  ╚═╝╚═╝     ╚═╝  ╚═╝╚═╝  ╚═══╝
```

<p align="center">Developed by Suyash Kumar // <a href="https://github.com/NEQULA-io">NEQULA</a></p>

<p align="center">
  <a href="#-🅣-thinkpad-fan-control-with-thinkfan">Overview</a> |
  <a href="#-features">💡 Features</a> |
  <a href="#-quick-start">🚀 Quick Start</a> |
  <a href="#-contribution">🤝 Contribution</a>
</p>

# <p align="center">🔴 🅣 ThinkPad Fan Control with ThinkFan</p>

A clean and comprehensive walkthrough for configuring **```ThinkFan```** on supported **```ThinkPad```** models.

Control your ThinkPad fan manually and dynamically. This `ThinkFan` based setup gives finer thermal management, quieter operation, and greater control. This project documents everything from setup to advanced tweaks.


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


For full installation help, see [Autostart](docs/autostart.md) and [Persistent Control](docs/persistent-control.md).


## 📜 License

See [```MIT LICENSE```](LICENSE) for details.🔭 Track the Cosmos. Unveil Orbital Insights.


## 🤝 Contribution

We welcome community pull requests with:

- Configs for new ThinkPad models

- Custom profiles for low-noise or aggressive cooling

- Safety improvements and documentation updates

# 🎛 **Built in Slience for Performance and Full-Control.**
