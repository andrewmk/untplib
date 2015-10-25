# ntplib
Automatically exported from code.google.com/p/ntplib

Usage is as follows:

import untplib

c=untplib.NTPClient()
resp=c.request('0.uk.pool.ntp.org', version=3, port=123)
print("Offset is ", resp.offset)

from machine import RTC
import time

rtc = RTC()
print("Adjusting clock by ", resp.offset, "seconds")
rtc.init(time.localtime(time.time() + resp.offset))
