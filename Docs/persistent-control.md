# Ensuring fan control survives **`reboot`**

1. **Add kernel module to `initramfs`:**

    ```bash
    echo thinkpad_acpi | sudo tee -a /etc/initramfs-tools/modules
    ```

2. **Rebuild `initramfs`:**

    ```bash
    sudo update-initramfs -u
    ```

3. **Optional verification:**

    ```bash
    grep thinkpad_acpi /boot/initrd.img-$(uname -r) | strings
    ```
