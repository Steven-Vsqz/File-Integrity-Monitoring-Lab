# File Integrity Monitoring Lab
<!----------------------------------------------------------------------------------------------------------------------------------------------------------------------------->
## Table of Contents
- [Objective](#objective)
- [Utilities & Tools Used](#utilities--tools-used)

<!----------------------------------------------------------------------------------------------------------------------------------------------------------------------------->
## Objective

- [x] **Something

<!----------------------------------------------------------------------------------------------------------------------------------------------------------------------------->
## Utilities & Tools Used
![image](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![image](https://img.shields.io/badge/powershell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![image](https://img.shields.io/badge/VirtualBox-21416b?style=for-the-badge&logo=VirtualBox&logoColor=white)

<!----------------------------------------------------------------------------------------------------------------------------------------------------------------------------->
<details open>
<summary> 
  
## Title
</summary>

</details>
<!----------------------------------------------------------------------------------------------------------------------------------------------------------------------------->

<!--
Use ` for code

For badges
https://github.com/alexandresanlim/Badges4-README.md-Profile?tab=readme-ov-file#-ide-

Image holder
<img src="https://github.com/user-attachments/assets/3cc9cc2f-8c98-43d6-8922-eab02499c3e8" style="height: 55%; width: 55%;">

Insert website to text
[Tenable Nessus](https://www.tenable.com/products/nessus)

For TOC
## Table of Contents
- [What are Macros?](#macros-in-a-nutshell)
- [Instructions](#instructions)
- [List of Macros]()
  - [Cornugon Smash](#cornugon-smash)
  - [Healing Spell & Potion Tracker](#healing-spell-and-potion-tracker)
  - [Sneak Attack](#sneak-attack)
  - [Targeted Token Info](#targeted-token-info)

-->



<h1 align="center">File Integrity Monitoring Lab</h1>

This project demonstrates a File Integrity Monitoring (FIM) system using PowerShell and WinSCP on a Windows homelab setup. The lab includes a monitoring machine and a target machine, where file integrity is monitored based on NIST standards.

<div align="center">
<img src="https://github.com/user-attachments/assets/3cc9cc2f-8c98-43d6-8922-eab02499c3e8" style="height: 55%; width: 55%;">
</div>

<div align="center">
<h2>🛠️Utilities & Tools Used</h2>

![image](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![image](https://img.shields.io/badge/powershell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![image](https://img.shields.io/badge/VirtualBox-21416b?style=for-the-badge&logo=VirtualBox&logoColor=white)

</div>
<details open>
<summary><h2>👨‍💻Project Overview</h2></summary>

In this homelab, I set up a File Integrity Monitoring (FIM) system with the following goals:

- Use PowerShell to monitor critical files on a Target VM.
- Automate file integrity checks and generate alerts using Event Logs and daily reports.
- Transfer logs to a Monitoring VM for centralized logging using WinSCP.
- Ensure the setup aligns with NIST incident detection standards (NIST SP 800-53) for Incident Detection (SI-7).
 
</details>

<details open>
<summary><h2>💻Setup</h2></summary>

I set up two Windows virtual machines on an internal network and gave each a static IP address. I also mounted a shared folder between them for easy access.

On the target machine, I ran a script that creates a baseline SHA256 hash for all the files in a specific folder. In this case, the folder is: `C:\Users\Host\Documents`, which has 4 files. 

<img src="https://github.com/user-attachments/assets/ec218ffc-137b-405e-be1a-dd62f126fdcd" style="height: 85%; width: 85%;">

These are the ones I'll be monitoring, and the hash info gets logged into a .txt file.

<img src="https://github.com/user-attachments/assets/4945754f-e237-431d-a6d5-b2acce3b92e1" style="height: 85%; width: 85%;">

Next, I ran another script that checks the files’ integrity by re-hashing them and comparing it to the original baseline. If anything changes, it throws an alert.

I am storing the logs here `C:\FIM`:

<img src="https://github.com/user-attachments/assets/fe4d16b0-03a0-45f5-8658-9c594cc8f44a" style="height: 85%; width: 85%;">

Once both scripts were set up, I scheduled the integrity check script to run daily so everything gets checked regularly.

<img src="https://github.com/user-attachments/assets/915e6120-66b0-431e-b140-f8f56cfb796b" style="height: 45%; width: 45%;">

For log transfers, I installed WinSCP on both machines, which let the monitoring machine access the target’s directories. I set up a script to generate a daily summary report based on the logs and scheduled it with Task Scheduler.

After everything was ready, I made some small changes to two files: Staff and Client List. When I ran the integrity check, the log showed alerts for the exact files I had modified.

<img src="https://github.com/user-attachments/assets/50335f60-72b8-46a1-9956-70bce4848288" style="height: 85%; width: 85%;">

The log results:

<img src="https://github.com/user-attachments/assets/dd15e621-f2b2-4dcf-a842-c61370b954d0" style="height: 85%; width: 85%;">

The differance in hashes:

![image](https://github.com/user-attachments/assets/296005b0-1366-47f0-904d-b6af95f5fb57)

</details>






