# Decrease Swap Usage

> [!NOTE]
> Skip this step if you're not using a **swap** parition.

Decrease swap use so it uses the RAM more often than the storage drives. Once you've modified the configuration then reboot the system to apply changes.

```
$ cat /proc/sys/vm/swappiness

$ sudo nano /etc/sysctl.conf
vm.swappiness=10
```