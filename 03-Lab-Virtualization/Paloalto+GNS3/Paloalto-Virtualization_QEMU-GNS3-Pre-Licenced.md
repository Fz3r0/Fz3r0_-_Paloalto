# 🔥🧱🛡️ `Paloalto Virtualization` - `GNS3` + `QEMU`

![My Video](https://user-images.githubusercontent.com/94720207/165892585-b830998d-d7c5-43b4-a3ad-f71a07b9077e.gif)

### 🐦 Twitter  : [@fz3r0_OPs](https://twitter.com/Fz3r0_OPs)
### 🐱 Github  : [Fz3r0](https://github.com/fz3r0) 

---
 
#### Keywords: `Networking` `Network Security` `NetSec` `Blue Team` `Defensive Security` `PCNSA` `PCNSE` `Paloalto` `Firewall` `NGFW`

---

<br>

# 📝❓📄 `Index`

- [Introduction: Paloalto: GNS3 + QEMU](https://github.com/Fz3r0/Fz3r0_-_Paloalto/blob/main/03-Lab-Virtualization/Paloalto+GNS3/Paloalto-Virtualization_QEMU-GNS3-Pre-Licenced.md#%EF%B8%8F-introduction-paloalto-gns3--qemu)
- [Instructions](https://github.com/Fz3r0/Fz3r0_-_Paloalto/blob/main/03-Lab-Virtualization/Paloalto+GNS3/Paloalto-Virtualization_QEMU-GNS3-Pre-Licenced.md#-instructions)
- [Installation Result](https://github.com/Fz3r0/Fz3r0_-_Paloalto/blob/main/03-Lab-Virtualization/Paloalto+GNS3/Paloalto-Virtualization_QEMU-GNS3-Pre-Licenced.md#-installation-result)

## 🔥🧱🛡️ Introduction: `Paloalto: GNS3 + QEMU`

This guide provides step-by-step instructions to set up a Paloalto virtual firewall in GNS3 using QEMU. You'll learn how to download the required appliance and virtual firewall files, configure the GNS3 environment, and start working with the PA-VM template.

The process includes importing the Paloalto appliance, resolving missing files, and setting up the firewall for basic network connectivity. By the end, you'll have a functional Paloalto VM ready for testing and learning within your GNS3 environment.

## ❓ Paloalto: GNS3 + QEMU: `Instructions`

Start by downloading the necessary files and follow the instructions below to get your virtual firewall up and running!

### ⭕ 1. Download PA GNS3 Appliance + Paloalto Virtual Firewall

#### Appliance:

- https://gns3.com/marketplace/appliances/pa-vm

#### Paloalto Firewalls

- https://www.mediafire.com/file/fz68eqzye2hdfmd/virtioa.qcow2/file (v9.0.4)
- https://labhub.eu.org/UNETLAB%20II/addons/qemu/Palo%20Alto/ (v10)

### ⭕ 2. Installation:

1. Download `pan-vm-fw.gns3a`
2. Open GNS3 & Click on: `File > Import Appliance` 
3. Install on main server, next...
4. QUEMU binary, just click next...
5. Select the version of the **Paloalto Virtual Firewall** you want to use (in my case 9.0.4), next...
    - If is not showing green already and are "missing files" then:
    - Click `Import` (bottom left) and select the Virtual Firewall from your PC (eg. `virtioa.qcow2`).   
6. Click Finish and you will see `The appliance has been installed and a template named 'PA-VM 9.0.4' has been successfully created!`

The template will be available in the firewall category.

- **Default Username: `admin`**
- **Default Password: `admin`**

_PAN-VM goes through several iterations of host prompts during boot. This is normal and expected._

### ⭕ 3. Getting Started:

To configure a static IP address at the console enter the following commands:

````sh
configure
set deviceconfig system ip-address <Static IP> netmask <Netmask> default-gateway <Gateway IP> type static
set deviceconfig system dns-setting servers primary <DNS Server IP> secondary <DNS Server IP>
commit

````

## ❓ IMPORTANT: `For 10.0.4 or Any Pre-Licenced VM`

The pre-licenced VM's (eg. KVR 10.0.4) use a specified date generated when the file/licence was created, so it's no longer valid!

- https://upw.io/4xk/PA-VM-KVM-10.0.4.vm_eval.qcow2
- https://upw.io/4FK/PA-VM-ESX-10.0.4.vm_eval.ova

### ESXI .ova

Paste following settings in vmx or add them in `esxi`:

tools.syncTime = "FALSE"
time.synchronize.continue = "FALSE"
time.synchronize.restore = "FALSE"
time.synchronize.resume.disk = "FALSE"
time.synchronize.shrink = "FALSE"
time.synchronize.tools.startup = "FALSE"
time.synchronize.tools.enable = "FALSE"
time.synchronize.resume.host = "FALSE"
rtc.startTime = "1631486450"

### qcow2 QEMU

For qcow2, use "-rtc base=2021-09-12" in settings. You can change time back after it boots up. Also, it supports uploading dynamic updates files manually. 

![image](https://github.com/user-attachments/assets/b539695f-5b75-4d6e-92a8-021fb66ff2c2)

![image](https://github.com/user-attachments/assets/9f8c51a0-fc10-4fa7-b3a3-e3c8c1027315)

![image](https://github.com/user-attachments/assets/a2b3784a-6180-4e0e-8750-b26e8c059575)



**The way to work-around this issue using the GNS3 KVM or VMware .ova  is to manually changin the date to the GNS3 virtual machine:**

1. Disable the time on the Vmware:

    - Go to PA-VM or GNS3-VM host directory and add below lines to the `.vmx file` (eg `C:\Users\Fz3r0\Documents\Virtual Machines\GNS3 VM\GNS3 VM.vmx`), to completely disable the time sync:
    
````
      time.synchronize.continue = "FALSE"
      time.synchronize.restore = "FALSE"
      time.synchronize.resume.disk = "FALSE"
      time.synchronize.shrink = "FALSE"
      time.synchronize.tools.startup = "FALSE"
````

or

````
      time.synchronize.continue = "FALSE"
````

2. Start the VM from : Power -> Power on to Firmware

![image](https://github.com/user-attachments/assets/ecbcd7b5-97b0-44a6-8e92-fe570d4dc782)

3. From BIOS, change date to `01/01/2021` _(move with tab and arrows)_

![image](https://github.com/user-attachments/assets/d3f4dde8-008e-46c0-88a2-2ff44061e40c)

4- Save and Exit from BIOS `F10`

5- VM will come up and will not power off anymore, you can set NTP on the PA VM to have the correct time.

6- If you shutdown the VM and want to restart it again, repeat from step 3. 


## 📥 Importing the Paloalto Appliance

- Important: I will be using the `PA-VM 9.0.4` based on `QEMU` [INSTRUCTIONS FOR INSTALLATION](https://github.com/Fz3r0/Fz3r0_-_Paloalto/blob/main/03-Lab-Virtualization/Paloalto%2BGNS3/Paloalto-Virtualization_QEMU-GNS3-Pre-Licenced.md)

In the left side of GNS3 check for the new `PA-VM 9.0.4` in the `Security` devices: 

<span align="center"> <p align="center"> ![gns3](https://github.com/user-attachments/assets/1e3b431c-1e3f-4d08-a495-b0bb1dd495c1) </p> </span> 

- Before turning on the Appliance, add more RAM to it (8GB)

![image](https://github.com/user-attachments/assets/5fc29d61-7793-4de0-955e-80c23f593d43)

- Add the Appliance, a VPC, a NAT or Cloud and check for DHCP and connections (it's important to check the IP obtained for future uses).
- **Check from the PC for an Available IP for future use in the Paloalto, in my case `192.168.122.200` (No response: available IP Address)**

![image](https://github.com/user-attachments/assets/549f9dde-81e0-46b9-b754-7ee9612dc4ac)






## 📥 Log-In for first time

1. Enter the Paloalto Appliance via SSH (just double click) <br><br>
    - **YOU MUST WAIT SEVERAL MINUTES UNTIL THE `4TH PROMPT/RESTART` BEFORE YOU CAN LOGIN, BE PATIENT!!!**
    - **YOU WILL SEE PROMPTS LIKE: `"VM LOGIN"` OR `"PA HDF LOGIN"` OR `PANOS BOOT ERROR BLAH BLAH`, DON'T TOUCH ANYTHING, JUST WAIT!!!**
    - **IN MY CASE I'VE WATED MORE THAN 15 MINUTES WITH A MONSTER PC**
    - THE LAST PROMT IS CALLED **``**

2. Enter the default credentials `admin/admin`

3. Check the `show system info` and validate the 30 day licence:

````java
admin@PA-VM> show system info

hostname: PA-VM
ip-address: unknown
public-ip-address: unknown
netmask: unknown
default-gateway: 
ip-assignment: dhcp
ipv6-address: unknown
ipv6-link-local-address: unknown
ipv6-default-gateway: 
mac-address: 0c:e7:82:ba:00:00
time: Sat Sep 11 19:07:20 2021
uptime: 0 days, 2:07:08
family: vm
model: PA-VM
serial: 4C4C4508149EFCF
vm-uuid: CDE782BA-279D-4BD1-B7C7-850BDB12ECED
vm-cpuid: KVMEVL:63060000FDFB8B07:VMFlex30dayEval:us-west1
vm-license: 
eval-days-left: 30   <<<<-------------------||| 30 day evaluation active!! :D
vm-cap-tier: nolic
vm-cpu-count: 2
vm-memory: 4041648
vm-mode: KVM
cloud-mode: non-cloud
sw-version: 10.0.4.vm_eval
global-protect-client-package-version: 0.0.0
device-dictionary-version: 1-211
device-dictionary-release-date: 
app-version: 8408-6715
app-release-date: 
av-version: 0
av-release-date: 
threat-version: 0
threat-release-date: 
wf-private-version: 0
wf-private-release-date: unknown
url-db: paloaltonetworks
wildfire-version: 0
wildfire-release-date: 
wildfire-rt: Disabled
url-filtering-version: 0000.00.00.000
global-protect-datafile-version: unknown
global-protect-datafile-release-date: unknown
global-protect-clientless-vpn-version: 0
global-protect-clientless-vpn-release-date: 
logdb-version: 10.0.3
vm_series: vm_series-2.0.4
dlp: dlp-1.0.2
platform-family: vm
vpn-disable-mode: off
multi-vsys: off
operational-mode: normal
device-certificate-status: None
````


# 🏠📧🌐 Fz3r0 Lab Addressing

| **Parameter**         | **Value**            |
|------------------------|----------------------|
| **Network IP**         | `192.168.122.0/24`  |
| **Gateway**            | `192.168.122.1`     |
| **DHCP for VPC**       | `192.168.122.205`   |
| **DHCP for Paloalto**  | `192.168.122.200`   |


# 📚🗂️🎥 Resources

- https://www.youtube.com/watch?v=TbQxGUKgpg8
- https://youtu.be/VEZ5DZpQ_qc?si=uOT53KK6zI1mgiER
- https://labhub.eu.org/UNETLAB%20II/addons/qemu/Palo%20Alto/
- https://www.youtube.com/watch?v=VEZ5DZpQ_qc&list=PL9aktFItFNdOXy0Z-D5RFSdX_AHjJrIgi&index=1
- https://live.paloaltonetworks.com/t5/general-topics/pa-vm-10-0-4-deployment/m-p/502912#M105376
- https://www.youtube.com/watch?v=eUaVv6Hfc68

---

<span align="center"> <p align="center"> ![giphy](https://user-images.githubusercontent.com/94720207/166587250-292d9a9f-e590-4c25-a678-d457e2268e85.gif) </p> </span> 



&nbsp;

<span align="center"> <p align="center"> _I hope this information was useful for someone_ </p> </span> 
<span align="center"> <p align="center"> _and please, don't forget to enjoy your days..._ </p> </span> 
<span align="center"> <p align="center"> _...It is getting dark... so dark..._ </p> </span> 

&nbsp;

<span align="center"> <p align="center"> _In the mist of the night you could see me come, where shadows move and Demons lie..._ </p> </span> 
<span align="center"> <p align="center"> _I am [Fz3r0 💀](https://github.com/Fz3r0/) and the Sun no longer rises..._ </p> </span> 

---






---

> ![hecho en mexico 5](https://user-images.githubusercontent.com/94720207/166068790-fa1f243d-2db9-4810-a6e4-eb3c4ad23700.png)
>
> _- Hecho en México - by [Fz3r0 💀](https://github.com/Fz3r0/)_  
>
> _"In the mist of the night you could see me come, where shadows move and Demons lie..."_ 
