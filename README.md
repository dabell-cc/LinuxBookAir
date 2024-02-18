# LinuxBookAir
Fixes and finds while using linux on a 2015 MacBook Air

## Fixes
1. Keyboard **brightness keys** don't change the level (but do show the current brightness level overlay).  
   Observed: Keyboard backlight brightness keys work.  
   Observed: Play/Pause and valume media keys work.  
   Prerequisite: Clicking the battery icon (Power Manager Plugin) in the XFCE4 panel shows the brightness level, and changing it has the desired effect.  
   Prerequisite: `cat /sys/class/backlight/acpi_video0/actual_brightness` shows the numeric level.  
   Fix: Click the Power Manager Plugin Icon and select 'Settings...'. Under General>Buttons turn on 'Handle display brightness keys'. Set the step count (20-50 is reasonable).
   
1. Keyboard **brightness keys** steps are too big/small.  
   Fix: Power Manager Plugin step count is not the size of the step, but the number of steps between min and max.  
   Aka, setting 100 will result in a single press being an increment of 1. (0 to 100 in 100 presses).  
   Aka, setting 2 will result in a single press being an increament of 50. (0 to 100 in two presses).
   
1. **WiFi** not working.  
   Observed: `lspci | grep -i broadcom` shows BCM4360.  
   Observed: [https://pkg.kali.org/pkg/broadcom-sta#](https://pkg.kali.org/pkg/broadcom-sta#) no longer in the kali-Rolling repo.  
   Fix: [download broadcom-sta-dkms_6.30.223.271-23_all.deb](http://kali.download/kali/pool/non-free/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-23_all.deb) and install with `sudo dpkg -i <path_to_deb>`(might need `sudo apt install -f`?)  
   Observed: `sudo dkms stats` shows broadcom-sta/6.30.223.271, 6.6.9-amd64, x86_64: installed  

1. **WiFi** icon not showing correctly.  
   Observed: Icon showing in white, so it shows up well on the panel in dark mode, but is hard to see in light mode.
   Observed: Changing the icon size in the System Tray Plugin to something other than 22-23 changes the displayed icon.
   Observed: Setting XFCE4 Panel Dark Mode or Icon Size changes other icon, but not the System Tray Plugin icons.
   Fix: sorta... adjust the size of the System Tray Plugin to not be 22-23, or set auto size mode (iirc).  
   

## Finds
1. `ls /sys/module/hid_apple/parameters` shows some options for swapping control/command/fn/option keys.
2. 
