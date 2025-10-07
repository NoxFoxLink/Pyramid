# Pyramid - SDR-based FPV Video Detector/Decoder Software
In today's world, you don't need specialized equipment to receive different radio signals. Software-Defined Radio (SDR) devices act as flexible hardware that can capture a broad spectrum of radio signals. The magic happens with robust software processing, and Pyramid is built to decode analog FM-modulated video signals from FPV drones using your chosen SDR hardware. Pyramid is free to use but is not open-source software.
## Features
Please see this short demo \
[YouTube Demo](https://youtu.be/7acxQoPabEk)
## System Requirements
This version is optimized for Windows 11 and requires minimal system resources. For a comfortable experience, we recommend an Intel i7 CPU and at least 8 GB of RAM.
## Installation
- Visit the [Releases](https://github.com/NoxFoxLink/Pyramid/releases) section and locate the latest version.
- Download the zip archive, which contains a single folder with all necessary files.
- Extract the archive to a convenient location on your computer.
- Launch the software by running the pyramid.exe executable.
- Before detecting FPV video, configure your hardware as described in the section below.
## Hardware Setup
To receive FPV video signals, you need compatible SDR hardware with at least 10 MHz bandwidth and an appropriate frequency range. For example, the SDRPlay RSP1B receiver is a suitable choice. Pyramid uses the [SoapySDR](https://github.com/pothosware/SoapySDR) framework to communicate with SDR hardware, meaning it supports virtually any device compatible with SoapySDR. However, you must configure Pyramid before use.
### Configuring Pyramid:
Locate the **pyramid.cfg** configuration file, which is placed alongside the pyramid.exe executable. Add the appropriate SoapySDR initialization string to the pyramid.cfg file under the `SoapySDR_init_args` parameter. Typical initialization strings look like this: `driver=sdrplay,rfgain_sel=1,agc_setpoint=0` or, for remote setups `driver=remote,remote:rfgain_sel=1,agc_setpoint=0,timeout=500000,remote=tcp://192.168.1.1:55132`. Refer to the SoapySDR [documentation](https://github.com/pothosware/SoapySDR/wiki) and your hardware’s user manual to determine the correct initialization string for your device. Save the pyramid.cfg file with the updated configuration. A typical pyramid.cfg file looks like this: 
```
SoapySDR_init_args=driver=sdrplay,rfgain_sel=1,agc_setpoint=0
Scanner_SampleRate=10000000
SpectrumView_MaxVal=0
SpectrumView_MinVal=-80
```
Once everything is set up correctly, launch the software, and it will immediately begin scanning radio frequencies to detect the FPV drone's video signal. If the initialization string is incorrect or your hardware is malfunctioning, you may encounter an error message saying "Failed to init SDR hardware".\
*Note: Pyramid includes a few SoapySDR plugins: airspy, airspyhf, bladerf, hackrf, lime, redpitaya, remote, sdrplay enabling the use of corresponding hardware devices. For other devices, you may need to provide the appropriate SoapySDR plugin, which should be placed in the SoapySDRplugins subfolder.*
## Feedback
Don't hesitate to share your thoughts and ideas in the Pyranid Software discussion [group](https://groups.google.com/g/noxfoxpyramid).
