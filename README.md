# Amazon Air Quality Monitor Reversing <!-- omit in toc -->

[![License: CC BY-SA 4.0](https://img.shields.io/badge/license-CC%20BY--SA%204.0-blue?style=flat-square)](https://creativecommons.org/licenses/by-sa/4.0/)
[![Shop: Tindie](https://img.shields.io/badge/shop-Tindie-blue?style=flat-square)](https://www.tindie.com/stores/binary-6/?ref=offsite_badges&utm_source=sellers_Chrismettal&utm_medium=badges&utm_campaign=badge_medium)
[![Shop: Elecrow](https://img.shields.io/badge/shop-Elecrow-blue?style=flat-square)](https://www.elecrow.com/store/Binary-6)
[![Donations: Coffee](https://img.shields.io/badge/donations-Coffee-brown?style=flat-square)](https://github.com/Chrismettal#donations)

Reversing the Amazon Smart Air Quality Monitor to hopefully enable custom firmware.

**If you like my work please consider [supporting me](https://github.com/Chrismettal#donations)!**

## Table of contents <!-- omit in toc -->

- [Todo](#todo)
- [Background](#background)
- [Reversing](#reversing)
  - [FCC](#fcc)
  - [Devices](#devices)
  - [Pins](#pins)
    - [ESP32](#esp32)
    - [Header P1](#header-p1)
- [Custom Firmware](#custom-firmware)
- [Donations](#donations)
- [License](#license)

## Todo

- [ ] Teardown
- [ ] Uncap controller
- [ ] Take photos of internals
- [ ] List used sensors / actuators
- [ ] Trace pin assignments
- [ ] Find debug / upload interface
- [ ] IF debug info sent: Record some debug info of official firmware
- [ ] IF possible / easy: dump official firmware (Probably not)
- [ ] Create custom firmware (Or make [Tasmota](https://tasmota.github.io/docs/) compatible)

## Background

Amazon's [Smart Air Quality Monitor](https://a.co/d/j7YIuB0) is a device that measures your air for particulate matter, volatile organic compounds, carbon monoxide, as well as humidity and temperature. Some of these measurements are unitless and only show an index of 0-100, but that should be enough for many applications.

There is an LED on the top of the device which goes from Green via Orange to Red with sinking air quality.

It needs to be connected to your Wifi to function and seems to never publish its data locally. You can only get the measurement results through either the Alexa app or an Alexa device present in your house. This seems to rely on Amazon's servers to function.

Thus, there is no way to directly connect this sensor to [Home Assistant](https://www.home-assistant.io/) for example, or "airgap" the device for local-only operation.

The goal of this project is to find out what makes this device tick and possibly upload custom firmware to it, to get rid of Amazon's app and servers while enabling local operation.


## Reversing

### FCC

Since the device has RF capabilities, a lot of information is already found in the FCC database, where it is listed as [2AYXQ7327](https://fccid.io/2AYXQ-7327). I will not be rehashing information already found there.

### Devices

| Name | Class      | Type                     |
| ---- | ---------- | ------------------------ |
| U1   | Controller | `ESP32-PICO-V3`          |
| P1   | Air Sensor | Sensirion `SEN44 FDN-T`  |
| DS1  | LED        | RGB                      |
| S1   | Antenna    | Empty Plug + PCB Antenna |

### Pins

#### ESP32

| Pin Number | Device | Function |
| ---------- | ------ | -------- |
| 1          |        |          |

#### Header P1

![HeaderP1](/img/HeaderP1.png)

| Pin on header | Pin on other end | Function |
| ------------- | ---------------- | -------- |
| 1             |                  |          |
| 2             |                  |          |
| 3             |                  |          |
| 4             |                  |          |
| 5             |                  |          |
| 6             |                  |          |

## Custom Firmware

tbd

## Donations

**If you like my work please consider [supporting me](https://github.com/Chrismettal#donations)!**

## License

 <a rel="CClicense" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
