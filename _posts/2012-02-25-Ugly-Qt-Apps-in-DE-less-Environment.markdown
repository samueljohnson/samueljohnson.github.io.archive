---
layout: post
title:  "Ugly Qt apps in DE less environment"
date:   2012-02-25 6:45:10
category: Linux
---
If you are just using a Window Manager (WM) like openbox, awesome, etc without the full-fledged Desktop Environments (DE) like KDE, GNOME, etc, then applications build using Qt (VLC, Virtualbox, Google Earth, Scribus, etc) might look ugly. Like these:

<img alt ="Screenshot" src="/assets/img/Qt-without-Oxygen.png" width="100%">

A simple solution would be to:

1) Install Qt toolkit from your distro's repository.

2) Soft link oxygen.so from kde4 lib to qt lib.

{% highlight bash %}
sudo ln -s -T /usr/lib/kde4/plugins/styles/oxygen.so /usr/lib/qt/plugins/styles/oxygen.so
{% endhighlight %}

3) If you don't already have oxygen.so, download [this](http://www.mediafire.com/?ks227dbvcg9yan4) (64 bit, kde 4.8.0) to your /usr/lib/qt/plugins/styles directory.

4) Run 'qtconfig' and select 'Oxygen' theme.

Oxygen is the default theme for Qt apps. Other themes like GTK+ can also be selected if present.
