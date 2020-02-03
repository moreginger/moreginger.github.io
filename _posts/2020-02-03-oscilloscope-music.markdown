---
layout: post
title: Oscilloscope music and upgrading DS203
date: 2020-02-03 12:00:00 +0000
---

Recently, I was pointed at an [episode of Smarter Every Day on Oscilloscope Music](https://youtu.be/4gibcRfp4zA). I was a huge fan of Amiga Demoscene back in the day, and I got the same feeling listening to this and watching the trippy visuals. Of course, there's more, as the genius of this music is that the visuals are encoded in the sound, with nothing more than an X-Y plot of the L and R stereo channels. Hey don't get me wrong, the people doing these are genius to produce both the visuals and the sound from the same source.

### Scope upgradin'

Well, I've got a little digital scope so I figured it would be a fun to see whether I could get this to work. It's a few years old DS203 4-channel (DSO Quad), hardware version 2.60, and it was straightforward to get a standard 2-channel plot. Sadly the installed software wasn't up to doing an X-Y plot. But the internet provides:

|            |Old |New |
|------------|----|----|
|sys firmware|1.51|[B164](http://www.minidso.com/forum.php?mod=attachment&aid=MTQ5Nnw1ZTVhMGZhYXwxNTgwNzYyNDY4fDB8Njc%3D) [1]|
|app firmware|2.52|[WildcatV5.6](https://github.com/MotoMaxis/DS203-DSOQuad/tree/29d559a744569f944c651abbbffd272bc98b7474) [2]|

[1] See http://www.minidso.com/forum.php?mod=viewthread&tid=67&extra=page%3D1.

[2] Following the instructions in that repo to build the WildCatV5.6 folder.

Running dfu-mode and copying on the files should have been straightforward, but it didn't work on a modern Win10 box. This appears to be a common complaint with dfu when using anything newer than XP. I gave it a good try on Win10 and Ubuntu, using dfu-util (which never saw the device) and Zadag as [recommended by Scott Hanselman](https://www.hanselman.com/blog/HowToFixDfuutilSTMWinUSBZadigBootloadersAndOtherFirmwareFlashingIssuesOnWindows.aspx), but although the device happily showed up in dfu mode in Device Manager / dmesg, I couldn't apply the update. I resigned myself to getting access to an XP machine - luckily I know someone who keeps one around for exactly this kind of reason - and it worked first time with no issues :)

![spec with new firmware]({{site.url}}/images/2020-02-03-spec.jpg)

### Testing

Now you can tap off a signal with a 3.5mm lead (an unsoldered socket makes it easier if you have one).

![probe connections]({{site.url}}/images/2020-02-03-probe.jpg)

This scope has a lot of features and not much UI to control them with, there's lots of long press and short press magic to get everything. For my own reference: use ▲ to swap to the voltage range for CH(A) (200mv worked for me), then the left jog switch to set it. Move to CH(B) with the right jog switch, and set that the same way. Ignore the next two channels and the generator channel, then flip the 6th to X_Y, and the period to 2ms. That ought to be good enough to get a picture.

And here's a shot from "Blocks" by Jerobeam Fenderson. I got pretty good results by playing his YouTube videos, but the uncompressed wav files are noticeably better. You can buy them from [his site](https://oscilloscopemusic.com/). 

![blocks]({{site.url}}/images/2020-02-03-blocks.jpg)

### Next steps

I definitely need to split the audio signal so that I can put it into speakers as well. Turns out my existing splitter is acting as a L-R splitter... that explains why it was always so bad :D I have a new one on order to try.

It would be awesome to try and do this with an air gap, i.e. speakers + mics, but I don't think the signal quality is going to be good enough with the hardware I have access to. If I can get hold of a couple of good mics it might be worth a try.