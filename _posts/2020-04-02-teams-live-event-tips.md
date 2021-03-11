---
layout: post
title: Tips For Running Really Awesome Microsoft Teams Live Events
subtitle: What you need to know to make your Microsoft Teams Live Event stand out from the rest!
summary: What you need to know to make your Microsoft Teams Live Event stand out from the rest!
share-img: /img/livestream.jpg
image: /img/livestream_square.jpg
tags: [remote working, live events, streaming, Microsoft Teams, OBS, Voicemeeter]
comments: true
---

Over the last few months I've started to stream playing games on [Mixer](https://mixer.com/JimAmp). I've picked up a lot of knowledge along the way which has been hugely useful when putting together Teams Live Events, which I did this week with my colleague, and fellow streamer, [Eliott](https://mixer.com/8-Bit-Eliott). There are many parallels, it turns out. I've written this post in response to the number of questions I've had from people about the setup we used. So, here we go...

* TOC
{:toc}
## Things To Consider

Before we touch on software, hardware, tips, etc. there are some things to ask yourself before you go ahead with your event:

1. How many presenters will I have, where will they be (i.e. are they all remote, are you doing this from a single meeting room, a mix of both, etc.)?
2. How are you handling content? (i.e. will you be using a 'master deck' of slides, or will people be bringing their own content to share?)
3. Do you have enough supporting roles to make the event a success? (i.e. producers, Q&A moderators, etc.)
4. Do you need live interaction from your audience, or could you pre-record and have the advantage of being able to edit and process before sharing with people?
5. What's your budget? Some stuff covered in this post is not free, but is a worthwhile investment if you're serious about running live events frequently.

## Software

You can run a Teams Live Event just using Microsoft Teams - that's really all you need to get started. Teams will allow you to have producers, presenters and attendees and 'out of the box' provides enough to get you running an event. However, you're not here because you want to run 'just another Teams Event', you want a bit of polish, sparkle, you want your event to be the best! That's where some other magical bits of software can help:

1. [OBS Studio](https://obsproject.com/). This great bit of software can actually be used as an external encoder by Teams if you're running private or org-wide Live Events, but if you want to use it for a public event you'll want to consider something like the [Virtual Cam](https://obsproject.com/forum/resources/obs-virtualcam.539/) plugin. OBS gives you granular control over your video output and allows you to do things like fancy transitions, picture-in-picture, overlays, and all sorts of other cool stuff. If you're using the virtual camera then Teams will just see that as another webcam you can use, making it really simple to integrate. You might want to consider this if you're wanting to do a live demo where you want to overlay your actual webcam over the demo content, or you want to add a scrolling text banner to your video feed, or use stinger transitions to move between scenes, etc. <br><br> The thing to keep in mind is that OBS is great if you're the only one planning to present (i.e. because you're the only presenter, or because all your presenters are physically with you for the delivery of the event). What it won't allow you to do is apply those fancy effects to all your presenters who might be remote - and unless they're all a bit techy and install and set up OBS themselves, they'll only have what Teams has to offer natively to play with.<br><br> We came up with a compromise with our live stream, where I 'hosted and compered' the event, so I could kick off the stream with some fancy effects before handing over to presenters between their sessions. Having two producers made this much easier to orchestrate as Eliott could be in control of content, whilst I could be managing audio.

2. [Voicemeeter](https://www.vb-audio.com/Voicemeeter/index.htm). Specifically, I use Voicemeeter Potato but that might be more than you require. Voicemeeter is brilliant for managing audio. Teams only supports one audio input (i.e. your microphone). For most purposes, that's sufficient. However, in a Live Event you might want to play some interlude music, or bring in someone via a third party app such as Skype, or maybe even a hardware device like a phone, etc. Voicemeeter allows you to break out your audio inputs and determine what gets sent to one of a number of outputs. For example, I have my microphone, music apps, system sounds and voice chat apps (like Teams, Discord, in-game chat, etc.) all on separate inputs using Voicemeeter's virtual audio cables. I tell Teams to use one of Voicemeeter's outputs as it's input (i.e. as the microphone), and then I can use Voicemeeter to choose what gets sent to that output. For example, in our stream I sent my mic - so people could hear me speak - and music. When we went live with the stream I turned up the music fader and muted the microphone fader, and when I was ready to speak, I faded out the music and un-muted my mic. As far as Teams was concerned it's all just one audio feed.<br><br>It can take some time to get your head around Voicemeeter's various inputs, outputs, strips and buses, but I cannot recommend it highly enough for giving you a high degree of control over your audio sources and outputs.<br><br>I will freely admit this gave me the biggest headaches to get right - I resorted to drawing it out on a whiteboard. Now it's clicked it makes total sense, and was worth learning about, but I got myself into a right confused mess a few times first!

<center>
{% include youtubeplayer.html id="qXJ3NNgUVkE" %}
</center>
## Hardware

All you really need is a decent webcam and headset and you're all set - in fact, you don't even need a webcam if you're just doing audio over some slides. Why not spice it up a bit though? Make it really special? I've written about [all of the hardware I use](/2020/03/19/my-kit-2020/), which includes details of my microphone and audio interfaces so check that out if you want to know more. However, there were two bits of kit that were particularly useful:

1. [Elgato Stream Deck](/2020/03/19/my-kit-2020/#peripherals--other). This device beautifully integrates with OBS allowing you to control scenes, recording, streaming, and other settings - you can do so much with this little device it's very good value for money. The main thing this gives is convenience and better control. When you're live, the last thing you want to be doing is frantically switching between app windows searching for a button to do something. The Stream Deck sits barely a stretch of a finger away from my keyboard meaning that I don't even have to take my eyes off my webcam to switch scenes or content. Eye contact is super important when you're presenting as it helps people feel you're engaged and easier to watch. I have different screens configured for different purposes - such as when I'm streaming on Mixer, Teams, etc.

2. [Akai APC Mini](/2020/03/19/my-kit-2020/#audio--video). Arguably you need this device the least, and it's the most complicated to set up, but when it comes to providing a hardware interface to control Voicemeeter, it's brilliant. I have each fader on the device mapped in Voicemeeter, with the buttons mapped to different shortcuts (e.g. mute, fade up/down, controlling which outputs the input is currently being sent to, etc.).<br><br> This was a total luxury purchase, and plays to my inner geek. It looks cool on my desk, gives me ultra-convenience managing my audio inputs/outputs and levels, and was surprisingly helpful running the live event. For example, I programmed a macro that faded down a strip smoothly over 3 seconds, and back up over 3 seconds. This meant my music fade in/out was silky smooth and all professional-sounding. Before you know it, I'll be practicing my radio presenter skills, trying not to crash the lyrics on song intros...

## People

There are three core 'roles' on a Live Event: producers, presenters and attendees. You'll want to make sure you have people lined up to support you in the running of your event. Each person needs to focus on their role. In our event we broke it out:

- Eliott was responsible for switching between content. This meant that when it was time to hand over from one person to the other, he'd switch to the intro slide image, their video feed, etc. behind the scenes.

- I was responsible for the 'warm handover', I'd pick up from the outgoing presenter and do a brief intro of the upcoming one. This allowed Eliott the few seconds to make the changes smooth in the background without awkward pauses, allowed me to check the presenter was ready by having a few seconds chat with them, and hand over control of the slide deck to them. This worked because the content being presented isn't linked to the audio being broadcast insofar as I could speak over anyone, anytime which meant I could be the compere 'voice of God' whilst content was being switched around. (Important to note: this also means that presenters need to be on mute when they're not presenting otherwise they'll be heard!)

- Our colleague Guy was in the 'presenter' role, but focused on manning the Q&A panel to ensure the questions coming in were being answered as quickly as possible, rather than when Eliott or I had a chance. This was a really useful role to create as it makes attendees feel like there's great service being provided to them.

- I also coordinated with someone I knew would be watching the stream as an attendee. We had an open IM window throughout the whole event so that they could provide feedback about volume levels, whether content could be seen, etc.

## Tips

Here are some tips and gotchas we worked through which might save you some time:

1. Practice, practice, practice! Rehearse with your presenters, practice the handovers, check the settings all work in advance, on a separate stream! This is crucial if your presenters haven't done a Live Event before, but even if they have, coordinating in advance pays dividends when you do it for real. Every radio show, stage production, keynote speech, and primary school play is rehearsed. Your event should be, too.

2. Start your stream early and broadcast a placeholder image and some appropriately licenced music whilst you wait to 'go live'. It is much better to have a flying start to your stream than hitting "live" and then starting to speak. Starting a few minutes early allows you to check with your attendee mole that everything is working correctly and there have been no major problems. It's also a little twist of production polish that makes your event just a little bit better.

3. Teams only allows one person to share content at a time, but many people to share their video, or broadcast their audio. When one person shares their desktop, it will boot off anyone else who was already sharing. To work around this, we shared my desktop and 'gave control' of it to advance the slides to each incoming presenter. They could turn on their webcam in advance, ready for Eliott to switch over, but it avoided the jarring clash of sharing and unsharing desktops. This is where OBS and the Virtual Cam shine, because you can get around the limitation by effectively turning your webcam into a shared desktop by creating a scene in OBS which captures your desktop. It's pretty neat.

4. Have a "plan B" in case something goes wrong. This could be a holding slide, a backup copy of the deck, or a plan to switch to another presenter. When you're working with many remote presenters there's always the chance that one of them will experience a tech fail causing them to drop out of the event. Rather than let this derail your event, have a plan to switch to something as quickly as possible so the event can continue.