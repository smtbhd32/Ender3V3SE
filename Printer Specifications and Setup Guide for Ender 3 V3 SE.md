### Printer Specifications and Setup Guide for Ender 3 V3 SE

---

#### **Firmware Version**:  
The Ender 3 V3 SE currently runs **Marlin firmware v1.07**, compiled by [TomasekJ](https://github.com/TomasekJ/Ender-3V3-SE/releases). This version has been running smoothly with no major issues during the recent usage and testing.  

**Firmware Features**:  
- **Host Control**: The firmware has **Host Control** enabled, which provides more granular control over the printer directly from the OctoPrint interface. This feature allows users to adjust print parameters, perform maintenance tasks, and monitor the printer status with greater flexibility.
- **Auto Bed Leveling**: The printer is equipped with **CR Touch**, which enables **automatic bed leveling**. This system probes the bed at multiple points to create a mesh and compensates for any inconsistencies, ensuring better print adhesion and consistent first layers. Additionally, it supports **auto Z offset** adjustments for improved accuracy.

**Caution ⚠️**:  
- The firmware supports a maximum temperature of **300°C** for the hotend. However, the **stock hotend** can only handle temperatures up to **260°C**. Temperatures above 260°C may cause a **heat break** and damage the hotend. Therefore, **do not exceed 260°C** unless you upgrade the hotend to a higher-rated version.

---

#### **Remote Connectivity**:  
For remote connectivity and enhanced functionality, the printer is equipped with **OctoPrint**, which runs on a **Raspberry Pi Zero 2W**. The Raspberry Pi is connected to the printer via a **USB cable** and mounted on the left gantry of the printer. It is also fitted with a **Raspberry Pi Camera v1.3**, which moves along with the **Z-axis** during printing, allowing for remote monitoring.  

To control the printer remotely, we use **OctoApp** on Android devices along with the **OctoEverywhere** plugin, enabling access even when you're not connected to the same Wi-Fi network. 

Additionally, **Octolapse** has been installed on OctoPrint for creating time-lapse videos of prints, which works seamlessly, enhancing the overall experience.

---

#### **Power Loss Recovery**:  
A **power loss recovery plugin** has already been set up and is fully configured to handle interruptions during printing. You can find the complete guide for setting up and troubleshooting this plugin in the **Guides** folder of this repository.  

**How It Works**:  
- If a **power outage** occurs while a print is in progress and the **print command was issued from the printer**, the printer will display an option to **resume** the print when powered back on.
- If the **print command was issued from OctoPrint**, the plugin will generate a **recovery file** that can be used to resume the print from where it left off.

**Caution ⚠️**:  
- **Do not move the printer head manually** during or after a power loss. If the printer head is moved, the print cannot be resumed correctly, and the print will be lost. Always ensure the print head is stationary before allowing the recovery process to begin.

---

#### **Wi-Fi Connectivity & Access**:  
For accessing and controlling the printer remotely, you will need to connect to the Wi-Fi network with the following credentials:

- **Wi-Fi Username**: `admin`
- **Wi-Fi Password**: `admin1234`

To view the device connected to your Wi-Fi, look for an IP address assigned to a device named **simplypi**. Once you have the IP, simply type it into your browser to access the OctoPrint interface. The login credentials for OctoPrint are as follows:

- **Username**: `opmishra`
- **Password**: `Ender3V3SE`

Once logged in, you will have full control over the printer, including the ability to start/stop prints, adjust settings, and monitor print progress. For **remote control** outside the local Wi-Fi network, use **OctoEverywhere**, which provides full access to the printer from anywhere with an internet connection.

---

#### **Material Tested**:  
The Ender 3 V3 SE has been successfully tested with the following materials:

1. **Creality CR PETG 3D Filament 1.75mm (Black)**  
   [Link to purchase](https://robu.in/product/creality-cr-petg-3d-filament-1-75mm-1kg-black/)

2. **Creality Orange PLA+ 3D Printing Filament 1.75mm (White)**  
   [Link to purchase](https://robu.in/product/orange-pla-1-75mm-3d-printing-filament-1kg-white/)

Both materials have performed excellently with this setup, ensuring high-quality prints and reliable results. The **Cura profiles** for both materials are included in this repository, which can be easily imported into your slicing software for optimal print settings.

**Caution ⚠️**:  
- Store filament in **airtight containers** to prevent moisture absorption. If filament absorbs moisture, it may not print properly, leading to inconsistent extrusion or print failures. Ensure the material is properly dried before printing for best results.

---

#### **Ender 3 V3 SE Left Side Raspberry Pi Zero 2W & RPi v1.3 Camera Gimbal Mount**

For users looking to enhance their Ender 3 V3 SE with a Raspberry Pi Zero 2W and an RPi v1.3 Camera, you can mount these components on the left side of the printer. This upgrade adds remote monitoring and advanced features like camera integration, which can be used with OctoPrint for live video streaming and enhanced control.

 **Parts to Print**:
1. **Raspberry Pi Zero 2W Mount**
2. **Raspberry Pi Case**
3. **Camera Gimbal Parts** (for RPi v1.3 Camera)

You can download the 3D printable parts from the following link:  
[Ender 3 V3 SE Left Side Raspberry Pi Zero 2W & RPi v1.3 Camera Gimbal Mount - Printables](https://www.printables.com/model/1066230-ender-3-v3-se-left-side-raspberry-pi-zero-2w-rpi-v)

---

#### **Conclusion**:  
This setup provides a well-rounded 3D printing experience with remote capabilities, power loss recovery, and a fully automated bed leveling system. It ensures both ease of use and high-quality prints, making it ideal for both beginners and experienced users. The printer is now equipped for reliable, remote-controlled printing with full setup options via OctoPrint and custom firmware configurations.
