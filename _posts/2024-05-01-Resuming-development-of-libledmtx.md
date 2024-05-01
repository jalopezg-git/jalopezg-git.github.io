---
layout: post
title: 'Resuming development of libledmtx'
---

It has been a bit hectic in the last few months (and consequently a bit quiet here too).  Here is some news: after a long period without any functional changes, I'd like to announce that the addition of some new features in [libledmtx](https://github.com/jalopezg-git/libledmtx) is scheduled for the next few weeks.
Such features are mostly required for [p18-LEDcube](https://github.com/jalopezg-git/p18-LEDcube), but also useful for a future [p18clock](https://github.com/jalopezg-git/p18clock) firmware update.

Specifically, the planned features are:

- _Support for double buffer._  In this configuration, the driver reads from the frontbuffer, whereas the framebuffer manipulation routines act on the backbuffer.  Once the backbuffer is ready, buffers can be swapped by using `ledmtx_swapbuffers()`.
This in turn would enable viewports over the frontbuffer, i.e. having a frontbuffer larger than the actual display and only make a specific region visible.

- _Minor optimizations,_ mainly affecting the [r393c164](https://github.com/jalopezg-git/libledmtx/blob/master/src/driver/libledmtx_r393c164.S) driver.  Small memory savings in the access bank are also expected.

- _Introduction of tests based on lit and the gpsim Microchip PIC simulator_, enabling the validation of the library without relying on real hardware.

That's all for now!  Stay tuned!
