---
layout: post
title:  "Hide VMware Workstation while under Unity"
date:   2014-06-25 6:45:10
category: Linux
---

A while ago, I was testing out various desktop virtualization software. During evaluation, I installed VMware workstation on one of my (office) computer and I must say I love how the software works, indeed! And the Unity mode is a fun to play with! The fact that it lets you 'Alt-Tab' through all your virtual windows so seemlessly is just awesome. But, it has something that should be fixed:

As you enter Unity mode, the VMware player window minimizes to the taskbar. This window is confusing, OBSTRUCTIVE and is practically useless.

To fix this issue, on Linux with Openbox WM, add the following lines to your ~/.config/openbox/rc.xml

{% highlight bash %}

 <application name="vmware">
  <skip_taskbar>yes</skip_taskbar>
 </application>

{% endhighlight %}

On Windows: 

1. Download and install [PowerMenu](http://www.abstractpath.com/powermenu/)
2. Restart computer
3. Start VMware, and start unity
4. Minimize the screen with 'exit unity' button to taskbar (Important because else the window will steal focus when alt tabbing)
5. Right click on the task bar item and click 'Minimize to tray'

Enjoy real unity mode 
