# OCLog-v1.x

<p align="center">
Ligntweight and very minimalistic cross-platform Logger for ESDR3 (EE transceivers SS2/SS2Pro/DX)<br>
<br>
<img src="https://github.com/VK6NX/OCLog-v1.x/blob/main/images/mainview.png">
</p>

## Menu
- [Prerequisites](#prerequisites)
- [Installation](#install)
- [Config](#config)
- [Operation](#ops)
- [Release Notes](#rl1_3)
- [Roadmap](#roadmap)

---
## Prerequisites<a name = "prerequisites"></a>
- TCI 1.9 (or above)
- ESDR3
- EE transceiver model: SunSDR2 / SunSDR2 Pro / SunSDR2 DX. (Not tested with MB1 and QRP).
- OS: macOS 11.x/12.x/13x x64 (Intel or Silicon) / Win 10/11 x64 Intel / Linux Ubuntu 22.04

<ins>3rd party support:</ins>
Currently supports SDC prior ver15.24 via Telnet integration for 'Click on Call' function. In future (by end of 2022) update SDC support will be removed and replaced with EE native Skimmer.

<ins>Linux, Android and IOSsupport:</ins>
There is currently known issue with Linux-based static implementation. At this stage you have to compile and run dinamic App with Qt6.3.2 on you linux machine (note: Websockets library has to be present). We are looking to fix this issue ASAP, expected in Qt6.4.1 release.

As the App is developed with Qt6 framework, hence it can run on Android and IOS devices too (however at this stage we do not have Android and IOS versions publicly available; you have to compile it yourself from source).

Source code access requests are accepted via EE forum.
<br>
<br>

<b><i><ins>When to use this log</ins></i></b>
1. On portable computers (in DXpedition, field ops, etc), when you need everything - ESDR3, Log, Skimmer - to fit into single 16' desktop.
2. When power saving on the computer is critical (DXpeditions and field ops).
4. When minimum CPU/GPU consumption is the target.
5. When multiple OS (Win, Mac, Linux, Android, iOS) and hardware platforms (intel, arm) are in use

<b><i><ins>When NOT to use this log</ins></i></b>
1. When current Log is intended to become main QSO storage and keep all your QSO for the last 20 years. When sqlite db can easily grow up to 256,000 gibibytes, this log operates quick, well and as expected with up to 100K QSO records (exceeding 100K recods will not stop the log, but the the performance/power/CPU consumption cannot be guqrranteed).
2. When you need many extra features (rotator, panorama, direct access to cloud services from log, etc).
   
---
<br>

## Installation<a name = "install"></a>

<b>Important</b>: if you are migrating to 1.3 from previous version, please note that you have to re-enter Station data, CW macroses and double check setting parameters. This is due to refactoring Settings in v.1.3. If there is no intention to use v1.2 after installing 1.3, then corresponding v1.2 settings can be manually deleted from your OS (note that there is no automated cleanup for old versions settings removal, however old settings will not interfere with v1.3)  

### <ins>macOS:</ins>
- make sure you download version for your Mac processor type: intel or silicon
- unzip and move OClog app into Applications folder on your mac
- accept run in Security

### <ins>Windows:</ins>
- download Win archive
- unzip
- move folder to desired location at you computer
- run OC_log.exe

### <ins>Linux:</ins>
- compile from source under Qt6.3.2 dynamic

---
<br>

## Config<a name = "config"></a>
<p align="center">
<img src="https://github.com/VK6NX/OCLog-v1.x/blob/main/images/skimmer-settings.png"  width="50%" height="50%">
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
TCI-based automatic keyer support 4 sets of predefined and editable macros, 15 buttons each set.

Format is as following:<br>
<b>${MYCALL}</b> is the alias for own callsign (defined in Settings)<br>
<b>${RCVCALL}</b> is the alias for correspondent callsign (defined in CALLSIGN field<br>
<b>${SNDRST}</b> is the alias for RST sent to correspondent<br>
<b>${QSOID}</b> is the alias for current QSO number<br>

Macro setup example:<br>
<p align="center">
<img src="https://github.com/VK6NX/OCLog-v1.x/blob/main/images/cwmacro.png" width="50%" height="50%">
</p>
<br>

## Operation tips<a name = "ops"></a>
- It is advised to fill "Recommended" fields on Station Setup with valid data. This is because information from those fields is directly injecting into ADIF file.
- When using Log Mode, make sure you are selected most relevant mode to your current environment to avoid operations with unnissesary fields.
- It is recommended to export log to ADIF and clean the log before starting every new Contest or DXpedition. This is to keep proper QSO sequence numbering and prevent manual edit of the ADIF files at later stage (after ADIF export). Please note that this log was never intended as "main housekeeping storage of QSOs". (Opposite, this log assumes ClubLog or something similar is used as global storage.)

---
<br>

## Release notes for version 1.3<a name = "rl1_3"></a>
1. Minor bug fixes and functionality improvements:
 - Entering empty QSO record bug fixed. To record QSO by "Enter" key 3 characters required in CallSign field; by "Log" button 1 character required in CallSign field.
 - CW speed and CW macro Stop moved from the APP main interface to CW macro window.
 - DXCC list can now be updated by user (via Settings->DXCC). There is no option for user to add new or delete old DXCC entry (if this is needed, please log issue request)
 - ADIF fields compliance with version 3.1.3 ADIF specification verified (as per https://adif.org/313/ADIF_313.htm)
 - 3.1.3 ADIF Contest list embedded
 - Log duplicates verification implemented: App displays warning under CallSign field if the following condition matched: 'CallSign', 'Band' and 'Mode' parameters already present in the log. Important - duplicate check does not verify the Date at this stage, this functionality will be added later. Hence, it is recommended to export ADIF on daily basis for contests.
 - SRX, SRX_STRING, STX and STX_STRING parameters implemented in App interface (reflecting in ADIF export)
 - Common, DXpedition, IOTA DXpedition and Contest modes implemented (under "Mode" menu in Settings)
 
 
2. App Settings refactored:
- Critical setting moved to sqlite database
- Database location (OS dependent):<br>
-- macOS: $HOME/Library/Application Support/[Program Name]/QML/OfflineStorage/Databases/<br>
-- *nix: $HOME/[Username]/.local/share/[Program Name]/QML/OfflineStorage/Databases/<br>
-- Windows: Users\[Username]\AppData\Local\[Program Name]\QML\OfflineStorage\Databases<br>
(for further details on settings location see https://doc.qt.io/qt-5/qsettings.html#platform-specific-notes)<br>


## Upcoming feature set roadmap<a name = "roadmap"></a>

This log is in active development at current (as of Oct 2022) moment. It is lined up with ESDR3 development, works with every ESDR3 alpha release and targeting full log functionality by the ESDR3 v.1.0 release.

- EE native Skimmer (and EE-based Dev version) seamless integration (ETA end of Oct'22). And the same time Telnet will be superseeded by TCI.
- SSB macros (ETA early '23)

