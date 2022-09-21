# OCLog-v1.x

<p align="center">
Ligntweight and very minimalistic cross-platform Logger for ESDR3 (EE transceivers SS2/SS2Pro/DX)<br>
<br>
<img src="https://github.com/VK6NX/OCLog-v1.x/blob/main/images/skimmer1.png" width="50%" height="50%">
</p>

---
<ins>Prerequisites:</ins>
- TCI 1.9 (or above)
- ESDR3
- EE transceiver model: SunSDR2 / SunSDR2 Pro / SunSDR2 DX. (Not tested with MB1 and QRP).
- OS: macOS 11.x/12.x/13x x64 (Intel or Silicon) / Win 10/11 x64 Intel / Linux Ubuntu 22.04

<ins>3rd party support:</ins>
Currently supports SDC prior ver15.24 and prior via Telnet integration. In future (prior end of 2022) update SDC support will be removed and replaced with EE native Skimmer.

<ins>Linux, Android and IOSsupport:</ins>
There is currently known issue with Linux-based static implementation. At this stage you have to compile and run dinamic App with Qt6.2.3 on you linux machine. We are looking to fix this issue ASAP.

As the App is developed with Qt6 framework, hence can run on Android and IOS devices too (however at this stage we do not have Android and IOS versions publicly available; you have to compile it yourself from source).

Source code access requests are accepted via EE forum.
---

## Installation

### <ins>macOS:</ins>
- make sure you download version for your Mac processor type: intel or silicon
- mount .dmg and move OClog app into Applications folder on your mac
- accept run in Security

### <ins>Windows:</ins>
- download archive
- unzip
- move folder to desired location at you computer
- run OC_log.exe

### ins>Linux:</ins>
- compile from source under Qt6.3.2 dinamic

---

## Config
<p align="center">
<img src="https://github.com/VK6NX/OCLog-v1.x/blob/main/images/skimmer-settings.png" width="50%" height="50%">
</p>

<ins>ADIF support:</ins>
Log exported in ADIF v3.1.2 (Clublog supported format) into local directory specified in <i><b>'Settings-Log Info-Path'</i></b>
<br>
<br>
<ins>General config:</ins>
<i><b>'Settings-Station'</i></b> actual info is required to fulfill data into ADIF

<ins>IP connections:</ins>
<i><b>'Settings-Connection'</i></b> specifies local or remote TCI(ESDR3) and Telnet(SDC 15.24 and below) connectivity

<ins>CW macto:</ins>
TCI-based automatic keyer support 4 sets of predefined macros, 15 buttons each set.

Format is as following:
<b>${MYCALL}</b> is the alias for own callsign (defined in Settings)<br>
<b>${RCVCALL}</b> is the alias for correspondent callsign (defined in CALLSIGN field<br>
<b>${SNDRST}</b> is the alias for RST sent to correspondent<br>
<b>${QSOID}</b> is the alias for current QSO number<br>

Macro example:<br>
<img src="https://github.com/VK6NX/OCLog-v1.x/blob/main/images/cwmacro.png" width="75%" height="75%">
