+++
date = "2016-05-08T17:10:02+02:00"
draft = false
title = "Arduino Pro Mini FTDI: Programmer is not responding"

+++

> TL;DR Always make sure to have your TTL to USB adapter configured correctly.


As I started my very first Arduino based project, you can read about it [here]({{< relref "climbing-wall-timekeeping-project-00.md" >}}), I encountered some issues.

I decided to write a blog post seperate from the main series, because this topic
is not specific to the project and maybe some other people out there encountered
the same difficulties with getting their Arduino Pro Mini up and running.

## The Problem

So I plugged my Programing Adapter `FT232RL` into the Arduino board and the
USB plug into my computer[^1].

The green LED on the board lit up, and the red LED on pin 13 flickered. All
LEDs on the FT232RL board lit up as well. All seemed fine, the serial device
was up at `/dev/cu.usbserial-A94ZFXPH` and could be selected inside the Arduino IDE.

But as soon as I hit upload errors were starting to fill the console:

```
avrdude: stk500_recv(): programmer is not responding
stk500_getsync() attempt 1 of 10: not in sync: resp=0x00
avrdude: stk500_recv(): programmer is not responding
stk500_getsync() attempt 2 of 10: not in sync: resp=0x00
...
```

I spend a lot of time googling around, a lot of people seem to had a similar problem,
but all the propsed fixes didn't work for me, I also installed the latest FTDI driver,
you can get them [here](http://www.ftdichip.com/Drivers/VCP.htm). But nothing worked.

I eventually came to the conclusion, that the problem had to do something with
my operating system, so I installed the Arduino IDE on my Debian laptop.

The result were disenchanting. The very same output.


So the quest for a solution continued. I even considered that my board came without
a bootloader, but I couldn't figure out how to verify this assumption.


At one point in time I looked back at the programmer and checked for any shorts
and the like. And then it struck me. I forgot to jump the voltage pins.

That was stupid. My package arrived with bend pins and some broken headers,
I just assumed, that they were spare headers for the programmer. As it turns out,
this assumption was false. They were jumpers to select the correct voltage, as
seen in this image:

![Header pins of the Programmer](/img/arduino-pro-mini-ftdi/jumper-pins.png)
_The slightly bend jumper pins_

In retrospect this should have been easy to detect. But during debugging it wasn't.

One single missing jumper were the cause of this problem. Fixed in two seconds by
adding the jumper between the 3.3V and center pin.

I understand that this will not solve the problem `programmer is not responding`
for everyone, but if it helps just one of you out there, the time to write this
post was worth it.

[^1]: I am rocking a mid 2010 iMac with Mac OS X 10.9 running by the way.
