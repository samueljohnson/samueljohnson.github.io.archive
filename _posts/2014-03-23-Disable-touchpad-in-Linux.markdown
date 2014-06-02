---
layout: post
title:  "Disable touchpad in Linux"
date:   2014-03-23 6:45:10
category: Linux
---

One of the first thing I do whenever I install a new OS is to disable the annoying touchpad on the laptop. It always seem to get in my way while typing.

The following steps has been tested on Arch Linux, it should however also work on other distributions of Linux.

1) Find out the name of your touchpad device. Mine is "Elantech Touchpad".

{% highlight bash %}
$ xinput --list
⎡ Virtual core pointer id=2 [master pointer (3)]
⎜ ↳ Virtual core XTEST pointer id=4 [slave pointer (2)]
⎜ ↳ RAPOO RAPOO 5G Wireless Device id=11 [slave pointer (2)]
⎜ ↳ ETPS/2 Elantech Touchpad id=15 [slave pointer (2)]
⎣ Virtual core keyboard id=3 [master keyboard (2)]
↳ Virtual core XTEST keyboard id=5 [slave keyboard (3)]
↳ Power Button id=6 [slave keyboard (3)]
↳ Video Bus id=7 [slave keyboard (3)]
↳ Video Bus id=8 [slave keyboard (3)]
↳ Sleep Button id=9 [slave keyboard (3)]
↳ RAPOO RAPOO 5G Wireless Device id=10 [slave keyboard (3)]
↳ USB 2.0 UVC VGA WebCam id=12 [slave keyboard (3)]
↳ Asus WMI hotkeys id=13 [slave keyboard (3)]
↳ AT Translated Set 2 keyboard id=14 [slave keyboard (3)]
{% endhighlight %}

2) Replace "Your touchpad here" in the following script with the name of your touchpad device and save it as 'trackpad-toggle.sh'.

{% highlight bash %}
#!/bin/bash
if [ $(xinput --list-props "Your touchpad here" | grep Enabled | \
	gawk -F ':' '{ print $2 }') -eq 1 ]; then
xinput --set-prop "Your touchpad here" "Device Enabled" 0
else
xinput --set-prop "Your touchpad here" "Device Enabled" 1
fi
{% endhighlight %}

3) Make the bash script executable, run it and add it to your autostart list.
{% highlight bash %}
$ chmod +x trackpad-toggle.sh
{% endhighlight %}

4) Note that it is a toggle script. You can also assign a specific key binding to toggle touchpad on or off.
