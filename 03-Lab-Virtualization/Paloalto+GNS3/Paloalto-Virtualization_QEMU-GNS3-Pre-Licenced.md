# 🔥🧱🛡️ `Paloalto Virtualization` - `GNS3` + `QEMU`

![My Video](https://user-images.githubusercontent.com/94720207/165892585-b830998d-d7c5-43b4-a3ad-f71a07b9077e.gif)

### 🐦 Twitter  : [@fz3r0_OPs](https://twitter.com/Fz3r0_OPs)
### 🐱 Github  : [Fz3r0](https://github.com/fz3r0) 

---
 
#### Keywords: `Networking` `Network Security` `NetSec` `Blue Team` `Defensive Security` `PCNSA` `PCNSE` `Paloalto` `Firewall` `NGFW`

---

<br>

# 📝❓📄 `Index`

- [Instructions](https://github.com/Fz3r0/Fz3r0_-_Paloalto/blob/main/03-Lab-Virtualization/Paloalto+GNS3/Paloalto-Virtualization_QEMU-GNS3-Pre-Licenced.md#-instructions)
- Result

# 🔥🧱🛡️ Paloalto: `GNS3` + `QEMU`

This guide provides step-by-step instructions to set up a Paloalto virtual firewall in GNS3 using QEMU. You'll learn how to download the required appliance and virtual firewall files, configure the GNS3 environment, and start working with the PA-VM template.

The process includes importing the Paloalto appliance, resolving missing files, and setting up the firewall for basic network connectivity. By the end, you'll have a functional Paloalto VM ready for testing and learning within your GNS3 environment.

# ❓ Instructions

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

# 🟰 Installation Result

In the left side of GNS3 check for the new `PA-VM 9.0.4` in the `Security` devices: 

<span align="center"> <p align="center"> ![gns3](https://github.com/user-attachments/assets/1e3b431c-1e3f-4d08-a495-b0bb1dd495c1) </p> </span> 

# 📚🗂️🎥 Resources

- https://www.youtube.com/watch?v=TbQxGUKgpg8
- https://labhub.eu.org/UNETLAB%20II/addons/qemu/Palo%20Alto/
- https://www.youtube.com/watch?v=VEZ5DZpQ_qc&list=PL9aktFItFNdOXy0Z-D5RFSdX_AHjJrIgi&index=1

  
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