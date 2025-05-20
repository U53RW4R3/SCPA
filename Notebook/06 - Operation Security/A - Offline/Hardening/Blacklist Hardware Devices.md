# Blacklist Hardware Devices

## USB HID

> [!INFO]
> This prevents most of peripherals when plugging in through the USB port. Especially when it prevents BadUSBs to inject keystrokes.

Append a configuration file to blacklist USB devices with HID.

```
# echo 'blacklist usbhid' > /etc/modprobe.d/usbhid.conf
```

Apply the changes.

```
# update-initramfs -u -k $(uname -r)
```

---
## References

### Null Byte

- [Null Byte: Locking Down Linux - Using Ubuntu as Your Primary OS, Part 1 (Physical Attack Defense)](https://null-byte.wonderhowto.com/how-to/locking-down-linux-using-ubuntu-as-your-primary-os-part-1-physical-attack-defense-0185565/)