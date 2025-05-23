# Custom `config` tuned for modern ThinkPads (note - You can simply copy-paste the contents.):

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

- 🔍 Uses fan levels 0 to 7 (avoids `disengaged`)

- 🌡️ Relies on core temp sensors for thermal management

- 🎚️ Ensure sensors exist in sensors output
