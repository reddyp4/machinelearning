Installation instructions for nVidia Jetson Nano
1) Micro-USB Power supply needed: 5V-2A (Adafruit)
2) Download the Jetson Nano SDK SD Card Image
3) Write image to micro-SD card using Terminal
   > Open terminal app
   > List external devices:
    diskutil list external | fgrep '/dev/disk'
   > Insert micro-SD card
   > List external devices again: Now the additional disk is micro-SD (say diskx)
   > Remove existing partitions on the device
    sudo diskutil partitionDisk /dev/disk<n> 1 GPT "Free Space" "%noformat%" 100%
   > Write zipped SD card image to micro-SD card
    /usr/bin/unzip -p ~/Downloads/jetson_nano_devkit_sd_card.zip | sudo /bin/dd of=/dev/rdisk<n> bs=1m
   > While writing there is no indication. However after finishing mac throws a message that it cannot read the sd card - Click eject.
4) Setup and boot
   > Headless(no monitor) or usual mode
   > Remove power
   > Insert micro-SD card
   > Green-LED next to micro-USB connector must light up once booted
   > Jumper J48 power select header pins
   > Connect PC to Jetsons micro-USB port
   > Connect DC power supply to J25 power pack
   > Allow 1 min for boot-up
   > Open terminal
    > Check serial devices
     > ls /dev/cu.usbmodel*
    > Connect macOS PC to Jetson and check whats changed
    > ls /dev/cu.usbmodem*
    > ls -l /dev/cu.usbmodel*
5) 