---
layout: post
title: Making a soil moisture sensor with the Raspberry Pi 2
tags: [Python, Raspberry Pi, programming]
comments: true
bigimg: /img/soil_cropped_big.jpg
image: /img/soil_cropped_small.jpg
share-img: /img/soil_cropped_small.jpg
---

It's been a while since I did <a href="http://www.jamesbmarshall.com/2015/04/python-4-bit-led-counter-on-raspberry-pi-2/">anything productive</a> with my Raspberry Pi 2, but my recent purchase of a Yucca made me think about how I could use it for something intelligent, like Making a soil moisture sensor with the Raspberry Pi 2. This post is really aimed at saving you a lot of time hunting around for all the information you need. I had to browse a tonne of sites to find all the bits and pieces, but eventually I got it all to work as I expected.

First of all, the hardware. I had some bits and pieces lying around already; mainly some connecting wires and a spare breadboard. The only two components I had to buy were:
<ul>
 	<li>The sensor itself, available from Amazon.</li>
 	<li>An MCP3008 analogue to digital converter, also <a href="http://www.amazon.co.uk/gp/product/B00NAY3RB2?psc=1&amp;redirect=true&amp;ref_=oh_aui_detailpage_o01_s00" target="_blank" rel="noopener">available from Amazon</a>.</li>
</ul>
<h2>Goals for a Soil Moisture Sensor</h2>
I had a few key things this soil moisture sensor project should deliver:
<ol>
 	<li>It had to read the moisture level in a pot of soil.</li>
 	<li>It should record the moisture level and time stamp in some useful format, like CSV.</li>
 	<li>It should tell me, somehow, the readings as it makes them. Like a Tweet, etc.</li>
 	<li>It should be simple enough for me to make!</li>
</ol>
Since I had to wait for the additional hardware to arrive, I set about building the Python script that was going to make this all happen. I knew I needed to find out how to manipulate CSV files, <a href="http://www.cyberciti.biz/faq/howto-get-current-date-time-in-python/" target="_blank" rel="noopener">work with the date and time</a>,&nbsp;<a href="http://www.makeuseof.com/tag/how-to-build-a-raspberry-pi-twitter-bot/" target="_blank" rel="noopener">interact with Twitter</a>, use the <a href="https://www.raspberrypi.org/documentation/hardware/raspberrypi/spi/README.md" target="_blank" rel="noopener">SPI interface of the Raspberry Pi</a>, <a href="http://www.raspberrypi-spy.co.uk/2013/10/analogue-sensors-on-the-raspberry-pi-using-an-mcp3008/" target="_blank" rel="noopener">work with analogue sensors</a>, and <a href="http://raspberrypihq.com/how-to-share-a-folder-with-a-windows-computer-from-a-raspberry-pi/" target="_blank" rel="noopener">share files with other computers running Windows</a>.
<h2>Code</h2>
This is the Python script I came up with. I should point out that the articles linked previously in this post played a&nbsp;<em>huge</em> part in helping me to write this. Some bits I borrowed directly, and other bits modified or built upon. This script won't work if you just copy and run it. You'll need to follow the various guides to install and configure certain things, enable SPI, etc. but once you have, this should run.

```python
#!/usr/bin/env python
import sys
import os
import datetime
import csv
import spidev
import time

#Open SPI bus
spi = spidev.SpiDev()
spi.open(0,0)

# Function to read SPI data from MCP3008 chip
# Channel must be an integer 0-7
def ReadChannel(channel):
adc = spi.xfer2([1,(8+channel)&lt;&lt;4,0])
data = ((adc[1]&amp;3) &lt;&lt; 8) + adc[2]
return data

#Function to convert data into a standard range
def ConvertMoisture(data):
moist_reading = (data * 100) / float(1023)
moist_reading = round(moist_reading,1)
return moist_reading

#Set up CSV file for writing to
csv_out = open('readings.csv','a')
mywriter = csv.writer(csv_out, delimiter=',')

#Twitter details
from twython import Twython
CONSUMER_KEY = '&lt;YOUR KEY&gt;'
CONSUMER_SECRET = '&lt;YOUR SECRET&gt;'
ACCESS_KEY = '&lt;YOUR ACCESS KEY&gt;'
ACCESS_SECRET = '&lt;YOUR ACCESS SECRET&gt;'

api = Twython(CONSUMER_KEY,CONSUMER_SECRET,ACCESS_KEY,ACCESS_SECRET)

i = datetime.datetime.now()

#Get the time and date
timestamp = i.strftime('%H:%M:%S')
date = i.strftime('%Y/%m/%d %H:%M:%S')

#Get the sensor data
moisture = ReadChannel(0) #Reads CH0 from the MCP3008 chip
moisture_level = ConvertMoisture(moisture) #Normalises the reading from 0-1023 to 0-100
moisture_level = str(moisture_level) #Converts from int to str for tweet.

#Optional testing loop to see realtime readings from sensor
#while True:
# moisture = ReadChannel(0)
# moisture_level = ConvertMoisture(moisture)
# print moisture_level
# time.sleep(0.5)

#Send tweet
api.update_status(status='@jamesbmarshall it is '+timestamp+', and my current moisture level is '+moisture_level+'.')

#Write-out new reading to CSV
data = [(date,moisture_level),]

for item in data:
mywriter.writerow(item)

csv_out.close()

#END
```

<h2>Wiring Up</h2>
When it comes to wiring up the hardware, I found myself getting confused. One negative of the wonderful Pi community is that it's not always clear when there's different versions of the Pi being referenced. Most of what I found to work with was not specifically for the RPi 2, so I found these two images particularly helpful; <a href="http://raspi.tv/wp-content/uploads/2014/07/Raspberry-Pi-GPIO-pinouts.png" target="_blank" rel="noopener">one to compare the GPIO pins between the different Pi versions</a>, and the other more <a href="https://www.element14.com/community/servlet/JiveServlet/previewBody/73950-102-4-309126/GPIO_Pi2.png" target="_blank" rel="noopener">detailed pinout for the GPIO on the RPi 2</a>.
<h2>Next Steps</h2>
Now that the basic soil moisture sensor proof of concept works, it's time to move to phase two. My next set of goals are:
<ol>
 	<li>Convert the breadboard to veroboard as a more permanent solution.</li>
 	<li>Build up some sample data for calibration of the sensor.</li>
 	<li>Implement some thresholds in the code: overwatered, too dry, etc. so that the Tweets can say something more interesting like "It's time to water me!".</li>
 	<li>Expose / inject the readouts into some kind of database (SQL Azure perhaps) so that I can use some machine learning to predict when the soil will dry out.</li>
 	<li>Add more sensors for light and temperature to get a better picture of what's happening to the plant.</li>
</ol>
&nbsp;