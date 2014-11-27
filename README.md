To attach DSI2PRO for ccd program you must follow some instructions below:
======================================================================
1. Install package 'fxload' from your linux repository
2. Copy attached file dsi2pro.hex into /lib/firmware/ or your preferred path
3. In udev rule replace the pattern path to this firmware by actual one
3. Copy udev rule into /etc/udev/rules.d/ or into /lib/udev/rules.d/
4. Add your ordinary user to 'video' group.
	# usermod -G video myuser
5. Restart udev
	# /etc/init.d/udev restart
6. Plug in DSI2PRO camera to you computer.

-------------------
    Some Notes
-------------------

Meade DSI II Pro CCD camera build on Cypress FX2 USB chip.
After plugin to USB this device have VID:PID=156c:0100. Then 'fxload' util
upload firmware to device, and device reset itselt. After re-enumeration
device have VID:PID=156c:0101. You may check correct uploading firmware
by 'lsusb' output. As sample:

maxim@maxim-GA-790XT-USB3:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1443:0005 Digilent 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 156c:0101                                                  <-- this
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

After USB re-enumeration device ready to work.
