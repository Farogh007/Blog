---
layout: post
title:  "Design your Timer Module to save electricity."
date:   2018-09-05
description: How would you like it if someone turned you ON and then Left. Let's design a very simple Timer circuit which will help you to reduce your monthly electricity bill.
---

<p class="intro"><span class="dropcap">I</span>ndia is the world's third largest producer and third largest consumer of electricity with 91% of Electricity coverage. Average electrcity consumed between 2017-18 is 1,149 kWh. India has surplus power generation capacity but lacks adequate infrastructure for supplying electricity to all needy people. Of the 1.4 billion people in the world who have no access to electricity, India accounts for over 160 million, some 32 million homes who have not access to electricity.
</p>

India's electricity sector is dominated by fossil fuels, and in particular coal, which in 2017-18 produced about three fourths of all electricity. However, the government is pushing for an increased investment in renewable energy. The National Electricity Plan of 2018 prepared by the Government of India states that the country does not need additional non-renewable power plants in the utility sector until 2027, with the commissioning of 50,025 MW coal-based power plants under construction and achieving 275,000 MW total installed renewable power capacity. Read [more..][WIKi]

#### Now: Why should we save Energy?
These are some biggest reason we should really think and make every effort to save energy.
* Yes, saving energy will save your money.
* In a bigger picture less electricity used means less fossils fuel burned and less carbon footprint.
* Every single unit you save counts, remember 32 million homes in India still don't have access to electricity.

One should adapt their behaviour to energy-saving lifestyles, switch off the equipments if it is not in use, use energy saving electrical appliances.

#### Timer Module

<img src="{{ '/assets/img/Timer_Module.png' | prepend: site.baseurl }}" alt=""> 

A timer device is a great way to save both money and energy around your home. During the winter time usually we switch ON the water geyser and left it running the whole day. Place this device with your water geyser and set timer for 30 min, it will automatically switch off the geyser. Simmilarly you can place it at diffrent places of your home such as exhaust fan, washroom lights, Room heater etc.

#### How it works?

This is a very simple circuit, it has a microcontroller [Atmega328][328], an AC to DC converter [HLK-5M05][HLK],  a [DIP][DIP] switch to select time, a push switch to turn on the device and an AC driving circuit having TRIAC & SCR Output Optocoupler [MOC3041M][MOC] and a [TRIAC-BT139-600E][BT139]. We have 4-bit DIP switch which we can programe to set the timing. Now we have selected the first switch of DIP which will turn off the device after 15Min. Connect the Device eg: a geyser at the output port of the device and connect AC Line at the input port of the device. Push the switch it will turn ON the device and after 15Min it will be automatically turned OFF.

<img src="{{ '/assets/img/AC_Timer.png' | prepend: site.baseurl }}" alt=""> 
The main component for AC switching circuit is MOC3041M Optocoupler which has a Zero crossover circuit and ensures smooth switch and a TRIAC-BT139 of 16A. A TRIAC is actually two SCRs back to back. An SCR works like a diode accept it has a trigger pin. When an SCR is forward biased it conducts just like a diode. When an SCR is revers biased it won't conduct util the trigger pin is activated. When the trigger pin is activated the SCR will conduct until the current and voltage across it go down to zero.  When push button is triggered the Microcontroller will check the DIP switch Setting for the desired delay and it will trigger the Led of MOC3041M through 470E resister. This will Trigger the gate of TRIAC and the device connected on th load will be ON. TRIAC is not really good for inductive load so, I have used Snubber circuit R5 and C4 so that we can operate it on inductive loads. The value of the R5 and C4 will depend on the inductive loads.

For more details, please refer the [schematics][Sch_Timer]. Download [Eagle][Eagle_Timer] Files!

### Code!

{% highlight cpp %}
    void setup() {
    
    // Start Monitor Serial for debugging purposes
    _MonitorSerial.begin(_MonitorBaudRate);
    
    // put your setup code here, to run once:
    _MonitorSerial.println("Configuring the pins ...");
    pinMode(_outSignal, OUTPUT);
    pinMode(_inSignal, INPUT);
    pinMode(D5 , INPUT);
    pinMode(D6 , INPUT);
    pinMode(D7 , INPUT);
    pinMode(D8 , INPUT);
    _MonitorSerial.println("Configuring _outSignal D9 to default of LOW ...");
    digitalWrite(_outSignal, LOW);
    _MonitorSerial.println("Configured!");
    }
{% endhighlight %}

[Download][code_Timer] the code.





[WIKi]: https://en.wikipedia.org/wiki/Electricity_sector_in_India
[MOC]: http://www.onsemi.com/pub/Collateral/MOC3043M-D.pdf
[BT139]: https://www.mouser.in/datasheet/2/848/bta316-600bt-1220964.pdf
[328]: http://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-7810-Automotive-Microcontrollers-ATmega328P_Datasheet.pdf
[HLK]: http://www.hlktech.net/product_detail.php?ProId=60
[DIP]: https://www.robomart.com/dip-switch-4-bit
[Sch_Timer]: https://github.com/Farogh007/Projects/blob/master/EMBEDDED_PROJECTS/TIMER_MODULE/EAGLE_FILE/Schematics.pdf
[Eagle_Timer]: https://github.com/Farogh007/Projects/tree/master/EMBEDDED_PROJECTS/TIMER_MODULE/EAGLE_FILE
[code_Timer]: https://github.com/Farogh007/Projects/blob/master/EMBEDDED_PROJECTS/TIMER_MODULE/TIMER_CODE/TIMER_CODE.ino