---
layout: post
title: Getting Started with Home Assistant
subtitle: Everything they don't tell you when you start out, and more!
summary: Everything they don't tell you when you start out, and more!
image: /img/home_assistant.png
tags: [home assistant, home automation, internet of things]
comments: true
---

Years ago, I saw a video on YouTube - [the emergency party button](https://youtu.be/nZIfIzNW9xM). In those three minutes I knew I wanted to get into home automation. The challenge back then was that it was technically complicated, expensive, and I didn't have the time or my own place. It went onto the wish list for "some time in the future". Roll forward a few years, and now home automation technology is abundant, inexpensive and more straightforward than ever to get started with. In this post, and others which will follow, I'll document my journey with Home Assistant - the incredible home automation platform that has become the source of much joy and frustration in my home automation safari.

## Why Home Assistant?

Since around 2015, I've had an increasing amount of 'smart technology' in my home. A Philips Hue lightbulb here and there, Amazon's Echos popping up in a copule of rooms, that sort of thing. Then, in 2017, when we finally bought out own place, I started to ramp up my plans. I installed tado smart heating, I bought a SmartThings hub and some sensors, Ring doorbells and floodlights... pretty quickly I had half a dozen apps on my phone just to control the basic functions of my house. You can imagine how well this went down with my wife! I did my best to use Alexa's routines functionality to automate some things (like turning on/off the TV, lights, etc.) but there was no escaping that nothing was really working together very smoothly.

I'd bought the SmartThings hub as a way to unify platforms and started playing wtih some more advanced scenarios. Let me save you some time - don't bother. SmartThings over-promises and under-delivers. The integrations are poor, relying far too much on community-driven efforts and poor documentation and a complex cloud-based interface. I had to have two versions of the SmartThings app on my phone just to manage everything. Adding devices was frustrating, the list goes on. If this is the best 'off the shelf' home automation platform out there, we're really in trouble.

Enter Home Assistant. After chatting with friend, colleague and [YouTuber Mark Deakin](https://www.youtube.com/channel/UC8BG2tfSslYVsL8FqVkxXzQ) about our shared interest and frustration with home automation, he suggested I check out [Home Assistant](https://www.home-assistant.io/). I must admit, at first glace it looked just as complicated as SmartThings and I wasn't sure that it would solve any more problems for me than anything else I'd tried. Couldn't hurt to give it a go though, right?

## Choosing your version

Home Assistant is complicated. Let's get that out of the way right now. If you're even a little bit technically minded, patient, and curious then I'd recommend it. If you like an easy life, turn back now. This is a platform experiencing rapid growth, things change frequently. Documentation isn't amazing, there's a lot of assumed knowledge and you will spend more hours than you'd care to researching, troubleshooting and inevitably restoring backup after backup as you change your mind about the right way to do things.

You can install Home Assistant in lots of ways. As a VM, as a Docker container, on a Raspberry Pi, an Intel NUC, and more besides. Each option has pros and cons - this is the first area that's poorly documented. In my first attempt I thought I'd give running it as a VM on Hyper-V a go. I had a home server with enough spare horsepower to host it, I liked the idea of that over 'another' Pi to manage, and it seemed to be well supported. WRONG. If you have any designs on using a Zigbee or Z-Wave dongle, or indeed any external USB device give Hyper-V a miss. Initially I didn't think I would need that type of functionality since I was just going to unify my many platforms, but I quickly saw the appeal of 'going native' and consolidating several cloud-based platforms into one locally-processed one. However, Hyper-V doesn't support USB pass-through, and unless you want to dive into the uncharted territory of trying to attempt USB over IP or other 'work arounds' it just isn't a viable option.

Next up, a Raspberry Pi. I had a few lying around from previous projects so I thought I'd stick in on there and see how I got on. No worries about USB pass-through anymore since it was running natively. Except the Raspberry Pi is underpowered (unless you're buying one with a decent amount of RAM; I was re-using a RPi 3) and because of its ARM nature, not everything is supported. For example, the rather awesome Visual Studio Code add-in doesn't work if you're hosting on a Pi. This was frustrating because I felt that this early disappointment would be a warning of more to come. Not to mention the non-existent power-management features on the Pi (when the power goes, it just cuts out), the fact that the SD card will take a beating due to all of the logging that happens, and that without a graceful shutdown there's increased risk of corruption and problems re-starting after an outage. There had to be a better way. Damn you Hyper-V and your lack of USB pass-through support!

On to VirtualBox. After a bit of reading up, VirtualBox seemed like it would do. I could still have my VM, but I'd have to make the switch from Hyper-V on my server, to VirtualBox. No big deal really since it would be the only VM on that box. After some early false-starts I felt I was finally onto something...

Turns out, USB pass-through is a pile of crap. Almost every day, despite having put the necessary configuration in place, I was having to restart Home Assistant or re-attach the dongle just to get it working. Turns out that even though VirtualBox supports pass-through, it's notoriously unreliable and unless you're going to run a type 1 hypervisor like ESXi, Proxmox or similar, you're going to hit issues. "To hell with this", I thought. So instead of finding yet-another-platform for hosting Home Assistant, I sought ways of taking out the Zigbee and Z-Wave functions and handling them another way (it crossed my mind for the briefest moment that maybe trying to ditch Hue and SmartThings was a bad idea). In the end, I ran deCONZ natively on the server, and used an external integration to bring it into Home Assistant. I set up the Z-Wave integration on a separate Pi through Docker, bring it in externally as well. This worked well for a while.

## Prepare to design and re-design many times

After getting VirtualBox settled, the Zigbee and Z-Wave integrations handled, and I'd calmed down from my rage at having to start over so many times, I set about unpicking the numerous platforms and rationalising down to as few as possible. Through this I managed to entirely remove SmartThings and Philips Hue's bridge from my setup. With the exception of my tado heating system and my Logitch Harmony Hub, I have no other bridges or third-party hardware reliance to communicate with any of my sensors, appliances, lights, and so on. It's all integrated and controlled through Home Assistant.

If you choose the same route, and I recommend it because it simplifies things overall, be prepared to re-write automations, re-configure dashboards and generally keep re-configuring your environment as device names change, integrations change and so on. It will take weeks, if not months, for your environment to 'settle'. One excellent feature of Home Assistant (through the Home Assistant Operating System at least) is the backup and restore confiruation capability. Backup often, restoring is easy enough and it saves a lot of pain.

## Have patience and faith...

The learning curve for Home Assistant can be steep, but if you've got a 'growth mindset' approach to learning and you like solving challenges then as frustrating as it can be, it's also a lot of fun. It's also a slippery slope. Scratching the surface of what can be done caused me to spend more money that I'd expected buying more sensors, switches and lights as I became excited at the idea of automating ALL THE THINGS.

## Current setup and top tips!

As I write this post, I've upgraded my old home server to a new QNAP NAS (a story for separate post). Home Assistant runs as a VM hosted on Virtualization Station, with Zigbee integrated directly using USB pass-through. Z-Wave is handled via the NAS through Container Station and is integrated externally. As part of a wider exercise I now have no Raspberry Pi's running home automation or other workloads. Even things like Pi-Hole are now containers on the NAS. 

My tips for anyone looking to start playing with Home Assistant:

- Accept that the first several attempts are likely to be written off and re-done. Don't become disheartened that it isn't a set-and-forget experience. It takes patience, practice and determination to make it work.

- Whilst it can be difficult, try to think about your longer term needs. If you know that you're going to invest further into home automation, consider investing in decent hardware to host it on. You can run it on low-power devices, you can compromise on functionality, but I think you'll be disappointed. Budget for something decent.

- You're going to learn a lot as you go. Personally, I've learned a lot about virtualisation, containers, Linux, reading error logs, how Zigbee and Z-Wave mesh networks work, Let's Encrypt, and more. Bookmark all the URLs you find useful because invariably you'll go back to them often. I didn't at first and ended up trying to 're-find' pages by trawling through my browsing history when I could've just created a collection of all the useful things I found - such as [how to connect to a container and run commands from within it to set up a password file for my MQTT broker](https://stackoverflow.com/questions/46742443/mqtt-server-in-docker-a-way-to-run-the-mosquitto-passwd-u-from-dockercompos).

I have so much more to write about my experience but I'll stop here for 'part one'. Stay tuned for further posts covering how I set up my containers, creating a touchscreen home control panel, why Z-Wave is expensive garbage, and more as I learn. Let me know about your experiences, tips and tricks in the comments.