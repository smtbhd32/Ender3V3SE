# **To set up your Ender 3 V3 SE printer profile in Cura**

### 1. **Access Printer Settings in Cura:**
   - Open **Cura**.
   - In the top menu, go to **Preferences**.
   - From the dropdown, select **Printers** > **Add Printer** (if not already added).
   - If your **Ender 3 V3 SE** is already added, select **Ender 3 V3 SE** from the list of printers.

### 2. **Modify the Start G-code:**
   - Once the printer is selected, click on **Machine Settings** (the wrench icon).
   - In the **Machine Settings** window, locate the **Start G-code** section.
   - Replace the default start G-code with the custom script you want to use:

   ```gcode
   ; Script based on an original created by tjjfvi (https://github.com/tjjfvi) 
   ; An up-to-date version of the tjjfvi's original script can be found
   ; here: https://csi.t6.fyi/
   ; Note - This script will only work in Cura V4.2 and above!
   ; --- Global Settings
   ; layer_height = {layer_height}
   ; smooth_spiralized_contours = {smooth_spiralized_contours}
   ; magic_mesh_surface_mode = {magic_mesh_surface_mode}
   ; machine_extruder_count = {machine_extruder_count}
   ; --- Single Extruder Settings
   ; speed_z_hop = {speed_z_hop}
   ; retraction_amount = {retraction_amount}
   ; retraction_hop = {retraction_hop}
   ; retraction_hop_enabled = {retraction_hop_enabled}
   ; retraction_enable = {retraction_enable}
   ; retraction_speed = {retraction_speed}
   ; retraction_retract_speed = {retraction_retract_speed}
   ; retraction_prime_speed = {retraction_prime_speed}
   ; speed_travel = {speed_travel}

   M220 S100 ; Reset Feedrate
   M221 S100 ; Reset Flowrate

   G28 ; Home

   G92 E0 ; Reset Extruder
   G1 Z2.0 F3000 ; Move Z Axis up
   G1 X10.1 Y20 Z0.28 F5000.0 ; Move to start position
   M109 S[material_print_temperature_layer_0] ; Wait for the hotend to reach the target temperature
   G1 X10.1 Y145.0 Z0.28 F1500.0 E15 ; Draw the first line
   G1 X10.4 Y145.0 Z0.28 F5000.0 ; Move to side a little
   G1 X10.4 Y20 Z0.28 F1500.0 E30 ; Draw the second line
   G92 E0 ; Reset Extruder
   G1 E-1.0000 F1800 ; Retract a bit
   G1 Z2.0 F3000 ; Move Z Axis up
   G1 E0.0000 F1800 ; Reset Extruder to start
   ```

### 3. **Modify the End G-code:**
   - In the **Machine Settings** window, scroll down to the **End G-code** section.
   - Replace the default end G-code with the following:

   ```gcode
   G91 ; Relative positioning
   G1 E-2 F2700 ; Retract a bit
   G1 E-2 Z0.2 F2400 ; Retract and raise Z
   G1 X5 Y5 F3000 ; Wipe out
   G1 Z10 ; Raise Z more
   G90 ; Absolute positioning

   G1 X0 Y0 ; Present print
   M106 S0 ; Turn off fan
   M104 S0 ; Turn off hotend
   M140 S0 ; Turn off bed

   M84 X Y E ; Disable all steppers but Z
   M300 S220 P1000 ; Play a beep at 220 Hz for 1000 milliseconds (1 second)
   G04 P1000 ; Dwell for 1000 milliseconds (1 second)
   M300 S440 P1000 ; Play a beep at 440 Hz for 1000 milliseconds (1 second)
   ```

### 4. **Save the Settings:**
   - After pasting the modified G-code in both **Start G-code** and **End G-code** fields, click **OK** to save your settings.
    ![image](https://github.com/user-attachments/assets/982e40a2-b9bd-4665-ac44-6cd6c7caa50f)
    ![image](https://github.com/user-attachments/assets/b0d465e0-13c5-40d5-a872-ebf0bf3878dc)



This way, you can add the **Ender 3 V3 SE** printer to Cura and modify the G-code without needing to go back later.
