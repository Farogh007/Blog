---
layout: post
title:  "BMS| Battery management system Data Logger"
date:   2019-09-15
description: This device is designed to log data from the BMS system from a car through CAN serial protocol. The device will send data to a mobile app through Bluetooth and then it will be sent to the server.
---

<p class="intro"><span class="dropcap">T</span>he transition from IC Engine to electric motoring is accelerating and, as demand starts to rise, more manufacturers are unveiling new electric cars.

Even today, We’ve various options if we want an electric vehicle (EV) – including cars such as the fabled Tesla Model 3, the compact Renault Zoe, the Hyundai Kona Electric SUV, Mahindra eVerito, Tata Tigor and popular Nissan Leaf.
Over the next several years the number of electric cars offered by manufacturers to rapidly grow in number. The Automobile Companies are investing huge amount of money into the electric vehicle and new start-up are also coming up with new design and ideas. Ather Energy is one of the best example who have launched Ather 450. Understanding the potential of EVs in India government has started many initiatives and working toward this sector, recently Andhra Pradesh government signed a Memorandum of Understanding (MoU) with Toyota Kirloskar Motor (TKM) under which the auto major would introduce its electric vehicles in Amravati, the state's upcoming capital city. EESL, a joint venture of state-owned firms under the power ministry planning to set up nearly 1,000 charging stations across the country, more than 50 charging station are currently operational in new Delhi and planning to expand in Noida and NCR.
</p>

<p class="intro">Now, the real challenge is educating people for the adoption of electric vehicles and the infrastructure such as charging stations, policies such as regulating e-waste which will be generated after the end-of-life of these vehicles.

This board is designed to solve these kinds of pressing issue and help in the adoption of electric vehicle. The device log battery parameters such as voltage, current, temperature, etc from a BMS system of a car. The device will be connected through CAN serial protocol and have a Bluetooth SOC which will be connected through an App. With the help of these data, the app can help the user to reach to the nearest charging station to charge the battery. This can help the charging station to decide where to put the station by analysing the data.
</p>

<img src="{{ '/assets/img/CAN_Logger.PNG' | prepend: site.baseurl }}" alt=""><center>Figure 1 BMS Data Logger</center>


#### Overall arcitecture
The architecture is based on four major building blocks and using these we can make an impact to solve the above mention problems.

The logger will be attached to the BMS inside the car through CAN bus and the data will be transmitted to the mobile app via Bluetooth, which will give all the insights of a BMS. Then the Data will be sent to the cloud service where all the analytical part will be handled. Finally, the data will be displayed on a centrally managed dashboard, which will help the user to analyse the data and using these insights they can take some actions.

<img src="{{ '/assets/img/layout.PNG' | prepend: site.baseurl }}" alt=""><center>Figure 2 Data Flow</center>

#### Data Logger
The device is based on SOC from NXP MKW35Z512VHT4. It is an ultra-low-power, highly integrated single-chip family that enables Bluetooth Low Energy version 5 and Generic FSK (at 250, 500 and 1000 kbps) connectivity for automotive, industrial and medical embedded systems. KW36/35 integrates an Arm® Cortex®-M0+ CPU, up to 512 KB Flash and 64 KB SRAM. It Support CAN which is directly interfaced with the TJA1057GT/3J and DB9 connector. The device will be powered with the BMS. It has unique serial id which will be used for device registration.

<img src="{{ '/assets/img/logger.PNG' | prepend: site.baseurl }}" alt=""><center>Figure 3 Logger Flow</center>

For more details, please refer the [schematics][Sch]. Download [Altium][Altium_Design] Files!

##### Cross Platform App

This app will be used to connect consumers and service providers. The device will collect the data and send it to the server. It will help the user to navigate through the nearest charging station, it can be used to pay the charging bills. Service providers can introduce reward points to the users which could be used while paying charging bills or purchasing a new battery.

<img src="{{ '/assets/img/app.PNG' | prepend: site.baseurl }}" alt=""><center>Figure 4   Mobile App</center>

#### Dashboard

This dashboard could be used by the organisation such as EESl, to analyse the data gathered through the logger. It will show the real-time vehicle load on the charging station, revenue generated through a particular station. Using this information they can identify the places where they can instal new stations.

<img src="{{ '/assets/img/dashboard.PNG' | prepend: site.baseurl }}" alt=""><center>Figure 5 Dashboard</center>


[Sch]: https://github.com/Farogh007/Projects/blob/master/CAN_Logger_V1I1/CAN_Logger_V1I1-Schematics.pdf
[Altium_Design]: https://github.com/Farogh007/Projects/tree/master/CAN_Logger_V1I1