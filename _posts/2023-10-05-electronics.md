---
layout: post
title: Electronics
date: 2023-10-05 16:00:00 +2000
categories: electronics
tags: pcb
---


## Shield A v1.1
[Shield-A GitHub](https://github.com/rsedak/Shield-A)


### **Bill of Materials**

| Qty | Item |
| ----------- | ----------- |
| 1 ea. | PCB |
| 9 ea. | 1K ohm 1/4W 1% Resistor (R1-R8, R13) |
| 2 ea. | 100 ohm 1/4W 1% Resistor (R9, R10) |
| 2 ea. | 560 ohm 1/4W 1% Resistor (R11-R12) |
| 4 ea. | 10K ohm 1/4W 1% Resistor (R14, R15, R17, R18) |
| 2 ea. | 18.2 ohm 1/4W 1% Resistor (R16) |
| 8 ea. | LED 3mm (D0-D7) |
| 4 ea. | RGB LED 5mm common Katode (D8-D11) |
| 1 ea. | 14x7.5mm passive electronic piezoelectric buzzer SE |
| 2 ea. | MOSFET BS170 |
| 1 ea. | 3386-P 10K potentiometer with knob |
| 1 ea. | RV09 10K potentiometer - long shaft |
| 1 ea. | 2.54mm pitch slide DIP switch 2-bit |
| 1 ea. | 6x6x4.3mm SPST Momentary push switch |
| 2 ea. | 6x6x10mm SPST Momentary push switch |
| 1 ea. | 1x16Pin 2.54mm Straight Pin Header - Black |
| 1 ea. | 1x10Pin 2.54mm Straight Pin Header - Black |
| 2 ea. | 1x8Pin 2.54mm Straight Pin Header - Black |
| 1 ea. | 1x6Pin 2.54mm Straight Pin Header - Black |
| 1 ea. | 1x4 pin 2.54mm Socket Connector |
| 1 ea. | 1x16 pin 2.54mm Socket Connector |
| 1 ea. | LCD 1602 HD44780 (pin 15 is anode, pin 16 is katode) |















## Shield A v2.1
















## Chriggle Weather Station

- Use an ESP32 board as the microcontroller/main board.
- Use the [DS18B20](https://parts.chriggle.com/en/part/12) temperature sensor.
- Maybe add a more advanced sensor like humidity
- Use an 1602 LCD screen to display all the information.
- Display both real-time information on the current weather with the DS18B20, and weather forecasts for the current day/next day.
- Display the time and date.
- Have an on-off switch/slide switch for controlling the LCD/whole board.