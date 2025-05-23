- Use `level 7` only temporarily for fast cooling

- Avoid `level disengaged` unless you fully understand the risks

- Monitor temps:

  ```bash
  watch -n 1 sensors
  ```

- Manual override for emergency cooling:

  ```bash
  echo level 7 | sudo tee /proc/acpi/ibm/fan
  ```

- Return to `BIOS`/`auto` control:

  ```bash
  echo level auto | sudo tee /proc/acpi/ibm/fan
  ```
