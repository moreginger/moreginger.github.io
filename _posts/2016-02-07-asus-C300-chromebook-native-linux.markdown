---
layout: post
title: Native Linux on Chromebook
date: 2016-02-07 12:00:00 +0000
---

If you want to get Linux on a Chromebook, then the awesome [crouton](https://github.com/dnschneid/crouton) should be first on your list. I've used it successfully for the about a year, but it has some drawbacks:

+ Keybinding issues - these can mostly be fixed with enough effort
+ Performance issues - you're asking the Chromebook to do a bit more with both ChromeOS and Linux running. It wasn't uncommon for the machine to seize up in Linux.
+ Docker - I couldn't get this to run. IAGTU that some people have managed it, but it seems to be a hairy story.

So, figured it was time to go all out and install a nice lightweight Linux on my Asus C300 Chromebook. This gives us the following dependency graph.

Install Lubuntu -> Legacy Boot -> SeaBIOS -> Enable BIOS write

Enable BIOS write
-----------------
![Write protect screw]({{site.url}}/images/2016-2-7-write-protect.jpg)
Yowsers! This requires you to open the Chromebook to remove a write protect screw :S I followed the guide [here](http://www.matws.org/c300/). It was fairly straightforward and everything looks like it did before, despite breaking some of the small clips holding the case together.

SeaBIOS
--------
Few Chromebooks come with Legacy Boot support, and the C300 is no exception. [John Lewis](johnlewis.ie/baytrail-release/) (not the UK retailer!) has build SeaBIOS for Baytrail Chromebooks and provided a very handy installer. *Read all the warnings on his site*. In particular, at the time of writing, you're going lose suspend functionality. I don't think this is a deal-breaker, because the power usage of Baytrail is so low with the screen off, but it's certainly a shame.

Legacy Boot
-----------
For some reason on this hardware, the keyboard is extremely flaky during boot and during the install. Some people mention using an external keyboard to work around this. I managed to trigger the boot menu by hitting ESC _immediately_ after the prompt appeared, not before and not more than once. I also had trouble finding a USB drive which would boot, eventually using an old 1GB drive.

Install Lubuntu
---------------
![Lubuntu is alive!]({{site.url}}/images/2016-2-7-lubuntu.jpg)
I haven't tried LXDE before, but the low specs of the C300 persuaded me to go with something really lightweight instead of GNOME/Unity. Tips - don't mess around with an i386 install, I figured it might be more performant, but immediately discovered that [Google are dropping support for i386 Chrome in April 2006](http://betanews.com/2015/11/30/google-killing-chrome-for-32-bit-linux/). Which is perfectly reasonable, but caught me out.

Thoughts
--------
I've found LXDE really nice, I'm pretty sure I prefer it to XFCE and it's even smaller, so that's a win. John Lewis' blog mentions that there are issues with sound. I did get it working by first using pavucontrol to disable the HDMI out, then alsamixer to judiciously unmute channels (never seen so many before). ![So many sound channels :S]({{site.url}}/images/2016-2-7-alsamixer.png). Specifically these 4; (Left|Right) Speaker Mixer (Left|Right) DAC.
