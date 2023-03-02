# mmxklipper
Klipper for the Mingda Magician X series ST 407 mainboard

**THIS IS FOR THE ST MAINBOARD ONLY**

**USE AT YOUR OWN RISK**

This is very much an alpha test.

The MMX uses a mcu STM32F407ZET6 192k ram 512k cache 168mhz with a custom boot loader, so modifications to the klipper code were needed to make the binary.  **THIS USES THE USB A port**, you will need an A to A cable and **YOU MUST block off the 5v pin** on the cable or there will be damage to the Pi or The MMX mainboard.

here is an example of an A to A cable: https://www.amazon.com/Monoprice-Male-24AWG-Cable-Plated/dp/B002KKZRYM/ref=sr_1_6?crid=2VWT8AOWJONDZ&keywords=usb+a+to+a&qid=1677765580&sprefix=usb+a+to+%2Caps%2C358&sr=8-6

Klipper was configured to use stm32f407 mcu 64k bootloader offset 8mhz clock and usb pa11/pa12 (usb a) as the config options.

the usb c port is on other pins. more work is needed. there is also usart 3 that needs to be tested.


Its far from ready but here is whats working and whats not:

**Working**
X&Y movement and homing

Z motion and homing

extruder & hot end

heated bed

Independent dual Z (this will allow for gantry self tram)

**Not Working:**
Z Probe

Not Tested:
SDcard
Usb C port
Z tilt
Touchscreen (mine is missing)

**Needed:**
Optimize movement
