# 🔥🧱🛡️ Paloalto: `Management Interface Configuration`

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

# 🔥🧱🛡️ Paloalto: `Management Interface Configuration`


## Fz3r0 Lab Addressing

| **Parameter**         | **Value**            |
|------------------------|----------------------|
| **Network IP**         | `192.168.122.0/24`  |
| **Gateway**            | `192.168.122.1`     |
| **DHCP for VPC**       | `192.168.122.205`   |
| **DHCP for Kali**      | `192.168.122.204`   |
| **STATIC for Paloalto**| `192.168.122.200`   |

## Paloalto Init Configs 

- Original Script

````
configure
set deviceconfig system ip-address <Static IP> netmask <Netmask> default-gateway <Gateway IP> type static
set deviceconfig system dns-setting servers primary <DNS Server IP> secondary <DNS Server IP>
commit
````

- Edit Custom Script

````
configure
set deviceconfig system ip-address 192.168.122.200 netmask 255.255.255.0 default-gateway 192.168.122.1 type static
set deviceconfig system dns-setting servers primary 8.8.8.8 secondary 1.1.1.1
commit
````

## Option 1: `Only for virtualized Labs like GNS3`

- Just add the script to the CLI without even connecting to the management interface (using douwbl click)

Test the results:

![image](https://github.com/user-attachments/assets/5e198601-ad42-4b89-8e26-26c87b49d6c6)

Enter the Dashboard:

![image](https://github.com/user-attachments/assets/7f4145de-4d4c-4e24-a637-f64212fa9328)

Use credentials (in my case `admin` / `Admin.,12345`)

![image](https://github.com/user-attachments/assets/a82faa10-e7a7-4421-88c9-4053d2f46542)

Check the Management Interface Configuration: 

![image](https://github.com/user-attachments/assets/1055b645-dd06-46c5-86a5-fd8e89ac54a0)


# 📚🗂️🎥 Resources

- https://www.youtube.com/watch?v=TbQxGUKgpg8
- https://youtu.be/VEZ5DZpQ_qc?si=uOT53KK6zI1mgiER
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

