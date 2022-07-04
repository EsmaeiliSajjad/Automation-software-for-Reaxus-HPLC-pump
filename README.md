# Automation-Software-for-Reaxus-HPLC-Pump
Automation software to control and monitor a HPLC pump from Teledyne SSI Technology
# Table of Centent
1. [Description](#1)
2. [Code](#2)
3. [Upgrade](#3) 

<a name="1"></a>
# Description
I am sharing a automation/instrumentation project that can be done, in case a controlling software is not provided by the manufacturer. The video is showing how you can control a "REAXUS M1 Class HPLC pump (made by Teledyne SSI Technology) using a computer via a USB cable. Controlling the pump can be achieved through either an Analog I/O channel, such as 4-20 mA or 0-10 V, or a USB port (Digital I/O). The first technique is known to be the simplest way and of course, needs a data logger/controller as an interface between the pump and computer to read the signals and convert them to data; however, the second option is much more advanced and can transfer different data via the VISA command without a data logger. In addition to these points, for every single data, such as pump flow rate or pressure, you need a specific virtual/physical analog I/O channel to monitor/control the pump. However, this problem can be tackled when the communication between the pump and computer is performed by VISA.
As you can see in the video, we read/write different data including:
1. Pump serial number
2. Firmware version
3. Flow rate
4. Pressure and limits.
Furthermore, the developed data acquisition software can record and calculate the cumulative volume of injected fluid from the pump. 

https://user-images.githubusercontent.com/108043716/177029159-69982be7-d1bb-4e46-8cd1-cc3278affada.mov

Fig. 1: Testing developed software for automation of HPLC Pump.
<a name="2"></a>
# LabView Code
LabView computer coding software is used here to write suitable code for pump control. Since the instrument is connected via USB to the computer, there is no need for further configuration to define the pump. The following figure shows a part of the developed code.

<img src="https://user-images.githubusercontent.com/108043716/177029063-94d9abe3-f0cf-40d3-a0e6-abc7f6dd3895.png" width="900" />
Fig. 2: LabView code for the automation software including control, monitor, and store data in formatted data file. 

In order to read and convert digital data to meaningful values, you should be familiar with buffer read and write concepts. In addition to this, the proper command should be specified to be sent to the instrument. Some of these commands do not return any value; however, additional string functions should be added to the code to properly encode the return buffer.
<a name="3"></a>
# Upgrades
This software can be upgraded for other applications.
