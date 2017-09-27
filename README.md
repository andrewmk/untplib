# untplib
A MicroPython NTP client for the WiPy board. Adapted from [http://code.google.com/p/ntplib](http://code.google.com/p/ntplib)

## Installation
Download and put `untplib.py` in your `/flash/lib` folder.

## Usage

```
import untplib

c=untplib.NTPClient()
resp=c.request('0.uk.pool.ntp.org', version=3, port=123)
print("Offset is ", resp.offset)

from machine import RTC
import time

rtc = RTC()
print("Adjusting clock by ", resp.offset, "seconds")
rtc.init(time.localtime(time.time() + resp.offset))
```

## Limitations
The WiPy board doesn't support floating point numbers so times are only dealt with in whole seconds.
