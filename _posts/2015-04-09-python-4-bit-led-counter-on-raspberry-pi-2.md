---
layout: post
title: How To Make a 4-Bit LED Counter on Raspberry Pi 2 using Py
tags: [programming, Python, Raspberry Pi]
comments: true
---

It was my birthday last month. Your lack of card and cake was noted, dear reader, but let's not dwell on it...

One of the presents I was most eager to get to grips with was my new <a title="Raspberry Pi 2" href="https://www.raspberrypi.org/products/raspberry-pi-2-model-b/" target="_blank">Raspberry Pi 2</a>! (It's a single-board computer roughly the size of a credit card) Now, I studied both GCSE and A-Level Electronics, but haven't done anything remotely related since I left school, so I figured I should start with the basics. After setting up Raspbian and fitting the device into its snug little case I set about figuring out how to turn on a single LED.

I won't bore you with that little exercise, this post is about how I wrote a 4-bit binary counter with a "heartbeat" made of 5 LEDs and some hastily (and probably shoddily) written Python.

<h2>Python 4-Bit LED Counter</h2>
Pasted below is the current version of the script I've written to count in binary - displayed by the LEDs - from 0 to 15. I am not an expert in writing Python scripts; in fact, it's more accurate to describe me as a total novice. I've written in other languages before; things like HTML, PHP, Visual Basic, BASIC, C++, C#, etc. so I am familiar with basic programming concepts but I'm pretty rusty.
<h3>The Logic</h3>
Very roughly I approached the project&nbsp;by thinking about it like this:
<ol>
 	<li>I need to count from 0 to 15 (i.e. 16 numbers).</li>
 	<li>I need to convert that somehow from decimal into binary.</li>
 	<li>I need to, bit by bit, figure out whether each LED should be 1 or 0 for each whole number.</li>
 	<li>I need to turn the LEDs on, or off, based on the bit they represent (0, 2, 4, 8 or the heartbeat) for the current number in the count.</li>
</ol>
There is probably a very simple way to reduce the 4 steps above into 2 but I'm not that good, yet. I should admit that this isn't the first stab, but the final steps after much thinking and experimenting. I decided to include a "heartbeat" LED to make it easier to identify when a number was incremented as the code currently builds the binary representation serially (i.e. one LED at a time) rather than in parallel (i.e. just flashing all 4 bits in one go). When I first ran the code I couldn't figure out whether I was actually counting accurately or whether I'd just made a bunch of LEDs turn on and off at random!

This threw up a separate issue around timing. It's well-known that the Raspberry Pi isn't best suited to time-sensitive applications, even for something this simple. The delays are by no means accurate and it can vary. An extension to this project is to build an astable 555 timer circuit to remotely trigger 1 second intervals.
<h3>The Python Script</h3>
This is the code after having been through one round of refactoring (of sorts).
```python
import RPi.GPIO as GPIO
import time

#Set up script to use the right pin configuration
GPIO.setmode(GPIO.BCM)
GPIO.setwarnings(False)

#Define some variables
LED_counter = 0                     #The current number in decimal
bit_counter = 0                     #The current bit
current_num = ""                    #The current number in binary
LED_array = [[17,0],[22,0],[6,0],[26,0]]        #The LED configuration array

Pin_array = [17,22,6,26,4]

#Set all the pins to outputs
for index in range(len(Pin_array)):
    GPIO.setup(Pin_array[index], GPIO.OUT)

#Reset all the pins to 0
def resetPins():
    for index in range(len(Pin_array)):
        GPIO.output(Pin_array[index], 0)

    time.sleep(0.3)
    return

#Turn the LEDs on or off
def makeitso(theLEDs = [], *args):
    LED_counter = 0

    while LED_counter &lt; 4:
        GPIO.output(theLEDs[LED_counter][0], theLEDs[LED_counter][1])
        LED_counter += 1
        time.sleep(.3)
    return

#Define the pin configuration by counting in binary and stripping out each bit, char by char.
while LED_counter &lt;= 15:
    resetPins()
        
    current_num = bin(LED_counter)[2:].zfill(4)

        while bit_counter &lt; 4:
            LED_array[bit_counter][1] = int(current_num[bit_counter])
            bit_counter += 1

        bit_counter = 0
    GPIO.output(Pin_array[4], 1)
    makeitso(LED_array)
    LED_counter += 1

GPIO.cleanup()
```

<h3>The Counter in Action</h3>
Here it is in action:

{% include youtubeplayer.html id="pmFQxSlr06Y" %}

<h3>Next Steps</h3>
There are some things I'd like to do before I consider this project complete:
<ul>
 	<li>Get the code as efficient as possible. I know I'm doing things in a really convoluted way.</li>
 	<li>Improve the accuracy of the timing either through a remote astable 555 timer, or some other timing method.</li>
 	<li>Build and display the current number in parallel rather than displaying it a single LED at a time.</li>
</ul>