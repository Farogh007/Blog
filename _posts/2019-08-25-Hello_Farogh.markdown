---
layout: post
title:  "Hello-Farogh | Driver board for raspberry pi screen"
date:   2019-08-25
description: This board is designed using Raspberry Pi compute module3 with Camera and display support.It has LAN and USB along with Mems stereo Mic and speakers.
---

<p class="intro"><span class="dropcap">T</span>his board contains Compute Module 3 the guts of a Raspberry Pi 3 (the BCM2837 processor and 1GB RAM) as well as an optional 4GB eMMC Flash device or SD card option for more space. The Pi 3 has a processor speed of 1.2GHz and runs at roughly 10 times the speed of the Pi 1 due to its quad-core CPU. This is all integrated on to a small 67.6mm x 31mm board which fits into a standard DDR2 SODIMM connector.The Flash memory is connected directly to the processor on the board.</p>

<p class="intro">The board has on board Mems stereo mic connected to the compute module using I2s. It has 20W stereo amplifier which takes analog signals from compute module. It has CSI and DSI bus for interfacing Camera and Display. This board can be easily mounted on screen and make the design simple and easy to use.
</p>

<img src="{{ '/assets/img/board.PNG' | prepend: site.baseurl }}" alt=""><center>Figure 1 Base Board</center>


#### Integrated Inter-ICSoundBus (I2S)
The Integrated Inter-ICSoundBus (I2S) is a serial bus interface standard used for connecting digital audio devices together.
 
The I2S component operates in master mode only. It also operates in two directions: as a transmitter (Tx) and a receiver (Rx). The data for Tx and Rx are independent byte streams. The byte streams are packed with the most significant byte first and the most significant bit in bit 7 of the first word. The number of bytes used for each sample (a sample for the left or right channel) is the minimum number of bytes to hold a sample.

##### General Features
* Interfacing raspberry pi screen using DSI Bus.
* Interfacing of raspberry pi camera using CSI Bus.
* 4-USB port with good power stability.
* Lan port.
* Push to on/off switch.
* RTC
* Stereo Mems mic
* 20W stereo amplifier

For more details, please refer the [schematics][Sch]. Download [Altium][Altium_Design] Files!

#### I2s Mems Mic SPH0645LM4H
<center><img src="{{ '/assets/img/Mems.jpg' | prepend: site.baseurl }}" alt=""></center><center>Figure 2 Mems SPH0645LM4H</center>

 This SPH0645LM4H microphone doesn't even have analog out, its purely digital. The I2S is a small, low cost MEMS mic with a range of about 50Hz - 15KHz, good for just about all general audio recording/detection. Instead of an analog output, there are three digital pins: Clock, Data and Left-Right (Word Select) Clock. When connected to Compute module, the 'I2S Master' will drive the clock and word-select pins at a high frequency and read out the data from the microphone. No analog conversion required!

#### Raspberry Pi I2s configuration

 We need to manually compile this and here is the [Link][adafruit_Link]. Go through each step carefully and test your microphone.

#### Raspberry audio configuration

The Raspberry Pi has two audio output modes: HDMI and headphone jack. You can switch between these modes at any time.

The following command, entered in the command line, will switch the audio output to anlogue.

amixer cset numid=3 1

We can also do the same using raspi-config: Sudo raspi-config

Go to the advance setting and change the Audio setting and press enter.

Now, your mic and audio are working you can install google assistant services and control IOT devices.
Follow the [Link][google_Assistant], Enjoy!

This design is completely open source, anyone can use it or modify it. Contact me if anybody needs help in designing.



[Sch]: https://github.com/Farogh007/Projects/blob/master/Hello%20Farogh/Design%20Files/Hello-Farogh-V1I0/Design%20PDF%20and%20STEP%20File/Schematics.pdf
[Altium_Design]: https://github.com/Farogh007/Projects
[adafruit_Link]: https://learn.adafruit.com/adafruit-i2s-mems-microphone-breakout/raspberry-pi-wiring-and-test
[google_Assistant]: https://developers.google.com/assistant/sdk/guides/library/python/
