# Battery Saver

> [!INFO]
> If you own a laptop I recommend configuring the battery consumption.

Install it according to your package manager.

```
$ sudo apt install -y tlp
```

Configure the settings.

```
$ sudo nano /etc/default/tlp
..[snip]..
# Enable audio power saving for Intel HDA, AC97 devices (timeout in secs).
# A value of 0 disables, >=1 enables power saving (recommended: 1).
SOUND_POWER_SAVE_ON_AC=0
SOUND_POWER_SAVE_ON_BAT=0

# Disable controller too (HDA only): Y/N.
SOUND_POWER_SAVE_CONTROLLER=N

$ sudo systemctl restart tlp
```