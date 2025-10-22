
# MS41 VIN Number Change

*An indepth explanation on how to change your VIN number on your MS41 ECU's*
**This guide applies to ECU's with Stock & Changed Rom's**

---

## 🧰 Prerequisites

- ⚡ WinKFP
- ⚡ BMW Coding Tool
- ⚡ NCS Expert
- ⚡ Ediabas
- ⚡ INPA 5.0.6
- 🧾 Daten Files
`You can find links to everything needed in this repository.`
---

## 🧪 Setup

### 1. Updating WinKFP's Daten files using BMW Coding Tool:
1. Select SP-Source
2. Input path to your E36 Daten files
```bash
├── E36 (SELECT THIS PATH)
│   ├── cfgdat
│   |── data
│   |── daten
│   |── ecu
│   |── format
│   |── kmmData
│   |── sgdat
|   └── work
|___
```
3. Towards the bottom of BMW Coding tool, set your default NCS Expert, Ediabas, and WINKFP.NFS Pathways
4. Click Update SP-Daten & DONT backup
5. Click Update WinKFP & DONT backup

You can now close BMW Coding tool, your WinKFP is now properly setup.
---
### 2. Open INPA:
Navigate into your MS41.1/2 Coding section and take note of your **assembly number**
---

## 🔹 Open WinKFP
1. Select Comfort Mode
2. Click *Enter ZUSB* & input your *assembly number*
3. Click OK once it is found. Integration position will always be "Unverbaut"
4. Click Enter VIN and paste in the VIN you want your ECU Changed to.
5. Click DONE
6. Click (F3) Program
7. It will direct you to flash it twice then it will say Flashing DONE.
8. Vin change is Complete!

### 🔸 Error 201 Wrong ECU Hardware Number 1406464 (BSU Not possible)
This error occurs when your ECU's Stock ROM is different than what is flashed currently. Followed by the error is a 7 digit number, which usually corresponds with your ROMS ECU SW Number. Take note of it.
- Open folder \EC-APPS\NFS\DATA - This is the directory for WinKFP, specifically where your Daten files are saved.
- If your ECU's stock rom is MS41.2 , open MDS412/MDS412.HWH with notepad | if it is MS41.1 , open MDS411/MDS411.HWH with notepad
- It will look like:
```bash
;Hardwarehistorie vom 28.01.2000 08:20
1438067A F , 1405854B F , 1406464C F , 1430144A F ;
```
edit the first entry with the ECU HW that came in the 201 error (mine was 1406464)
it will look like:
```bash
;Hardwarehistorie vom 28.01.2000 08:20
1406464 F , 1405854B F , 1406464C F , 1430144A F ;
```
Save the .HWH file and continue with step 🔹 Open WinKFP



## 🧾 License

MIT License — free to use, modify, and share.  
Credits to MS41 logger community for XML defs and protocol research.

---

## 🧠 Future Plans

- Add RPM, TPS, IAT display support  
- Use ST7701 round display  
- Add WiFi broadcasting (optional web dashboard)  
- Add data logging (CSV)

---

> For any questions, email: qaisdanish6@gmail.com
