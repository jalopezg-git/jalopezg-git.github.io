---
layout: post
title: Restoring the PCI configuration space of a device
---

Sometimes it's useful to be able to restore the registers comprising the configuration space of a given PCI device to a known state, e.g. by the boot loader (so that the booted kernel finds the device in a specific state).
To address this need, I wrote a simple script that generates a bunch of `setpci` commands compatible with `setpci(8)` (from the `pciutils` package) and GRUB2's `setpci` command.

{% gist f4a31e43183385315ccb3e63d0860a25 gen_restore_pciconf.sh %}

It takes a single argument in any of the forms taken by `lspci -s`, i.e. `[[[[<domain>]:]<bus>]:][<device>][.[<func>]]` that specifies the address of a device (or group of devices) whose configuration space is to be dumped, e.g.

{% highlight bash %}
# 0000:00:1f.3 is a 'Multimedia audio controller: Intel Corporation Tiger Lake-LP
#                    Smart Sound Technology Audio Controller (rev 20)' on my machine
$ sudo ./gen_restore_pciconf.sh 0000:00:1f.3
setpci -s 0000:00:1f.3 00=86 01=80 02=c8 03=a0 04=06 05=04 06=10 07=00 08=20 09=00 0a=01 0b=04 0c=10 0d=20 0e=00 0f=00
setpci -s 0000:00:1f.3 10=04 11=00 12=2d 13=3f 14=60 15=00 16=00 17=00 18=00 19=00 1a=00 1b=00 1c=00 1d=00 1e=00 1f=00
setpci -s 0000:00:1f.3 20=04 21=00 22=00 23=3f 24=60 25=00 26=00 27=00 28=00 29=00 2a=00 2b=00 2c=43 2d=10 2e=22 2f=1a
setpci -s 0000:00:1f.3 30=00 31=00 32=00 33=00 34=50 35=00 36=00 37=00 38=00 39=00 3a=00 3b=00 3c=ff 3d=01 3e=00 3f=00
setpci -s 0000:00:1f.3 40=00 41=00 42=00 43=00 44=10 45=00 46=00 47=00 48=ff 49=09 4a=fb 4b=00 4c=00 4d=00 4e=00 4f=00
setpci -s 0000:00:1f.3 50=01 51=80 52=43 53=c0 54=0b 55=01 56=00 57=00 58=00 59=00 5a=00 5b=00 5c=00 5d=00 5e=00 5f=00
setpci -s 0000:00:1f.3 60=05 61=00 62=81 63=00 64=18 65=0b 66=e0 67=fe 68=00 69=00 6a=00 6b=00 6c=00 6d=00 6e=00 6f=00
setpci -s 0000:00:1f.3 70=10 71=00 72=91 73=00 74=00 75=00 76=00 77=10 78=00 79=28 7a=10 7b=00 7c=00 7d=00 7e=00 7f=00
setpci -s 0000:00:1f.3 80=09 81=60 82=14 83=f0 84=10 85=00 86=40 87=01 88=00 89=00 8a=00 8b=00 8c=a1 8d=04 8e=01 8f=00
setpci -s 0000:00:1f.3 90=00 91=08 92=28 93=00 94=00 95=00 96=00 97=00 98=00 99=00 9a=00 9b=00 9c=00 9d=00 9e=00 9f=00
setpci -s 0000:00:1f.3 a0=00 a1=00 a2=00 a3=00 a4=00 a5=00 a6=00 a7=00 a8=00 a9=00 aa=00 ab=00 ac=00 ad=00 ae=00 af=00
setpci -s 0000:00:1f.3 b0=00 b1=00 b2=00 b3=00 b4=00 b5=00 b6=00 b7=00 b8=00 b9=00 ba=00 bb=00 bc=00 bd=00 be=00 bf=00
setpci -s 0000:00:1f.3 c0=02 c1=06 c2=02 c3=28 c4=00 c5=60 c6=80 c7=04 c8=00 c9=0c ca=a5 cb=82 cc=10 cd=00 ce=03 cf=00
setpci -s 0000:00:1f.3 d0=00 d1=0c d2=b5 d3=02 d4=10 d5=00 d6=03 d7=00 d8=00 d9=00 da=00 db=00 dc=00 dd=00 de=00 df=00
setpci -s 0000:00:1f.3 e0=00 e1=00 e2=00 e3=00 e4=00 e5=00 e6=00 e7=00 e8=00 e9=00 ea=00 eb=00 ec=00 ed=00 ee=00 ef=00
setpci -s 0000:00:1f.3 f0=00 f1=00 f2=00 f3=00 f4=00 f5=00 f6=00 f7=00 f8=b5 f9=0f fa=21 fb=01 fc=00 fd=00 fe=00 ff=00
{% endhighlight %}
