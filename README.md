# Automation-software-for-Reaxus-HPLC-pump
Automation software to control and monitor a HPLC pump from Teledyne SSI Technology
# Table of Centent
1. [Description](#1)
2. [Code](#2)
3. [Upgrade](#3) 

<a name="1"></a>
# Description
I am sharing a automation/instrumentation project that can be done, in case a controlling software is not provided by the manufacturer. The video is showing how you can control a "REAXUS M1 Class HPLC pump (made by Teledyne SSI Technology) using a computer via a USB cable. Controlling the pump can be achieved through either an Analog I/O channel, such as 4-20 mA or 0-10 V, or a USB port (Digital I/O). The first technique is known to be the simplest way and of course, needs a data logger/controller as an interface between the pump and computer to read the signals and convert them to data; however, the second option is much more advanced and can transfer different data via the VISA command without a data logger. In addition to these points, for every single data, such as pump flow rate or pressure, you need a specific virtual/physical analog I/O channel to monitor/control the pump. However, this problem can be tackled when the communication between the pump and computer is performed by VISA.
As you can see in the video, we read/write different data including, pump serial number, firmware version, flow rate, pressure and limits, for example. Furthermore, the developed data acquisition software can record and calculate the cumulative volume of injected fluid from the pump.. 

<img src="https://user-images.githubusercontent.com/108043716/177025967-07355563-a29a-46fb-8db6-046afeeff769.png" width="200" />

Fig. 1: Example of NI Relay Output Module 

**But is there any way to use a low-cost multi-function I/O device like USB-6001 with 15 digital I/O from National Instruments and use its digital output to control a relay directly?** The answer is **Yes** but you have to design a circuit board as a converter to get a digital output and control a relay which would be a source for power. We are not able to directly connect a digital output channel to a relay and control it, because of a low-amp/low-voltage output of a digital channel. The voltage of a digital output will change beween 0 and 3.3 V with a max current of 10-50 microamp which is not enough to run a relay, even low-power consumption. So, here, we are introducing a circuit board which uses a transistor (BD-139) as a driver of a mechanical relay (24 V). Now, we are able to take a digital output module and convert it to a Relay output. The maximum power depends on the specifications of the relay.

<a name="2"></a>
# Required Devices
In order to go with this project you should have the following items ready:
1. NI-6001 (Universal analog and digital I/O)
2. Actuator or Soleniod valve 
3. Circuit board as a conveter (described in this project)
4. 24 V power supply (other power supplies can be use such as 12V or 15V) 

<img src="https://user-images.githubusercontent.com/108043716/177025510-1c7571d7-4a0f-4f32-be89-a403b97a0c09.png" width="150" /> &emsp; <img src="https://user-images.githubusercontent.com/108043716/177026352-008c9eaf-ba27-4b26-84dc-d2752f9aa47c.png" width="150" /> &emsp; <img src="https://user-images.githubusercontent.com/108043716/177026484-89a79800-a4ca-45f3-b7e1-4f9955307be2.png" width="150" /> 
<a name="3"></a>
# Circuit Board Design
The followings are a list of items for the circuit board and convert one Digital Output Channel to a Relay Output Channel.
1. NPN Transister (BD-139)
2. 24V Electromagnetic Relay
3. LED light
4. Resistors (10 KOhm and 2.2. KOhm)
5. 16-pin Molex connector

a NPN transistor (e.g., BD-139) is used here where the Base is connected, in a series with 2.2 KOhm resistor, to a digital output channel of a Digital Output device. There is another resistor (10 KOhm) is connected between the Base and Emitter of the transistor. The coil of the electromagnetic relay is also connected to the positive pole (+24 V) and the collector of the transistor (GND). An LED light with a 10 KOhm resistor is connected parallel to the relay showing where the channel is ON or OFF. When a there is a digital signal goes into the Base on transistor, the transister will be truned on and the driver for circuit board of relay will be turned on as well.
The following figure demonstrates the desiged circuit board (PCB) for this purpose. The circuit board is designed in **Protel 99SE** software. Here only four channels are ready. 

<img src="https://user-images.githubusercontent.com/108043716/177025641-1acea2bc-d654-43c1-9f3b-6ef199509e5e.jpg" width="500" />
<img src="https://user-images.githubusercontent.com/108043716/177025663-3593d234-a6d0-4920-8bd1-6165b8377529.jpg" width="500" />

Fig. 2: Desigend Circuit Board for Relay Output Converter. 

<a name="3"></a>
# Supported Devices/components
The following components are supported by this converter:
1. Solenoind Valve (12-24V)
2. LED or other types of light.
3. Air-operated actuator
4. Other low Amp (<10 amp) devices
<a name="4"></a>
# Upgrades
The designed circuit board in this project is able to control up to 12 Relay Output channels. However, another version for 24 channels is also designed. Also, to support a high-amp device (e.g. Vacuum pump), you can change the type of relay to achieve this goal.
