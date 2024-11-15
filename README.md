# Ender3V3SE
### **Power Loss Plugin Configuration for Ender 3 V3 SE (OctoPrint Setup)**

#### **Scenario 1: Actual Power Loss Occurs**
- **Behavior**: If a power loss occurs, the printer will automatically raise the print head by 10 mm when a new print is started through OctoPrint. This ensures the print head does not interfere with the print bed after the power is restored.
- **Configuration**: Set the **Z Homing** value in the power loss plugin configuration to **10 mm**. This ensures that the printer moves the head up by 10 mm upon restart when a new print is initiated.
- ![image](https://github.com/user-attachments/assets/e8653bc8-c272-4e13-82e9-0f39e003ad0c)




#### **Scenario 2: No Power Loss (Power Remains On) and OctoPrint Disconnects**
- **Behavior**: If the printer remains powered on and OctoPrint gets disconnected for any reason and then reconnects, the print head will **not** move. It will remain at the last saved Z height.
- **Configuration**: In this case, the **Z Homing** value is not required. Instead, use the following G-code in the power loss plugin configuration:
- ![image](https://github.com/user-attachments/assets/359c01da-f198-4fa3-ad1f-512692216492)



---

This should now be clear and concise! Let me know if you need anything else.
