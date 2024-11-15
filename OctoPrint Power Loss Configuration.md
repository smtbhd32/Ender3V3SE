# **Power Loss Plugin Configuration for Ender 3 V3 SE (OctoPrint Setup)**

### **Scenario 1: Actual Power Loss Occurs**
- **Behavior**: If a power loss occurs, the printer will automatically raise the print head by 10 mm when a new print is started through OctoPrint. This ensures the print head does not interfere with the print bed after the power is restored.
- **Configuration**: Set the **Z Homing** value in the power loss plugin configuration to **10 mm**. This ensures that the printer moves the head up by 10 mm upon restart when a new print is initiated.
- **Note:** The cursor `" | "` should be placed on the next line.
  ![image](https://github.com/user-attachments/assets/fab8bab8-1466-424e-9d6e-f849dc248d28)


```gcode
G92 Z{adjustedZ}  ; set Z with any homing offsets 
;M211 S0 ; Deactivate software endstops
G91 ;relative positioning
G1 Z-{z_homing_height} F200 ; correcting Z_HOMING_HEIGHT
G90 ;absolute positioning
;M211 S1 ; Activate software endstops
```




### **Scenario 2: No Power Loss (Power Remains On) and OctoPrint Disconnects**
- **Behavior**: If the printer remains powered on and OctoPrint gets disconnected for any reason and then reconnects, the print head will **not** move. It will remain at the last saved Z height.
- **Configuration**: In this case, the **Z Homing** value is not required. Instead, use the following G-code in the power loss plugin configuration:
- **Note:** The cursor `" | "` should be placed on the next line.
  ![image](https://github.com/user-attachments/assets/c3352fe0-159f-4844-b7b0-05f65c8047d0)
  




---

If either of these scenarios arises and the proper settings were not initially configured, you can modify the recovery G-code file based on the settings provided above. Alternatively, if you prefer, you can intentionally turn off the printer to create Scenario 1 (no headache). This will trigger the 10 mm head raise and reset the configuration without any further adjustments.
