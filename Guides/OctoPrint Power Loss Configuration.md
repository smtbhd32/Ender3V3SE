# **Power Loss Plugin Configuration for Ender 3 V3 SE (OctoPrint Setup)**
This guide provides step-by-step instructions for configuring the **Power Loss Recovery Plugin** on your Ender 3 V3 SE through OctoPrint. It covers various scenarios where power may be lost to either the printer or OctoPrint, and outlines how to ensure reliable recovery and print continuity after power interruptions.

### **Key Topics Covered:**
1. **Power Loss Scenarios**: Learn how to handle different power loss situations, including when power is lost to the printer, OctoPrint, or both.
2. **Plugin Configuration**: Detailed setup for the Power Loss Plugin, ensuring the print head moves appropriately (e.g., raising 10mm) when a print is resumed after power loss.
3. **Recovery G-code**: How to implement and use recovery G-code to prevent print failures.
4. **Final Setup Recommendations**: Best practices for ensuring that your printer always recovers smoothly, without the need for frequent reconfiguration.

This guide will help you minimize material wastage, prevent failed prints, and save time when dealing with power interruptions during your 3D printing projects.

### **Scenario 1: Actual Power Loss Occurs**
- **Behavior**: If a power loss occurs, the printer will automatically raise the print head by 10 mm when a new print is started through OctoPrint. This ensures the print head does not interfere with the print bed after the power is restored.

### **Scenario 2: No Power Loss (Power Remains On) and OctoPrint Disconnects**
- **Behavior**: If the printer remains powered on and OctoPrint gets disconnected for any reason and then reconnects, the print head will **not** move. It will remain at the last saved Z height.

### **Scenario 3: OctoPrint Powered Out**
- **Behavior**: If OctoPrint loses power, it may cause a disconnection, and recovery could potentially involve re-establishing the connection and starting the print again. The print head will remain at the last saved Z height.

### **Scenario 4: Both Printer and OctoPrint Lose Power**
- **Behavior**: If both the printer and OctoPrint lose power simultaneously, the printer will raise the head by 10 mm when a new print starts, following the **Scenario 1** configuration. This avoids further complications and simplifies the recovery process.

### **Final Setup Recommendation**
- To avoid the need for frequent reconfiguration, it is **recommended to create Scenario 1** by intentionally turning off the printer. This will ensure that the head always raises by 10 mm when a new print starts, providing a reliable and consistent recovery behavior.

  ![image](https://github.com/user-attachments/assets/fab8bab8-1466-424e-9d6e-f849dc248d28)

- **Configuration**: Set the **Z Homing** value in the power loss plugin configuration to **10 mm**. This ensures that the printer moves the head down by 10 mm to compensate z_homing when a new print is initiated.
```gcode
G92 Z{adjustedZ}  ; set Z with any homing offsets 
;M211 S0 ; Deactivate software endstops
G91 ;relative positioning
G1 Z-{z_homing_height} F200 ; correcting Z_HOMING_HEIGHT
G90 ;absolute positioning
;M211 S1 ; Activate software endstops
```
- **Note:** The cursor `" | "` should be placed on the next line.


### **Caution**:
- **Do not move the printer head manually during recovery** in any of these scenarios. Let the printer head remain in its current position. Moving the head could cause the print to be unrecoverable, resulting in the loss of your progress.

---

### **Important Notes**:
- In case of any power loss scenario, whether to the printer or OctoPrint, first turn off the printer, then turn it back on. After that, run the recovery G-code file (as shown above) to ensure proper recovery.
- If the settings were not properly configured, you can modify the recovery G-code file based on the settings provided above.
- To avoid changing configurations repeatedly, **always create Scenario 1 by intentionally turning off the printer**. This ensures the printer raises the head by 10 mm on startup and resets the configuration without further adjustments.

---
