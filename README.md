# M5Stack-Raspberry-Pi-Integration
A complete method by which to integrate a Raspberry Pi Zero/ Zero W with an M5Stack, based loosely on the guide published by Yama-chan


Sources of code used:
https://github.com/m5stack/M5Stack/blob/master/examples/Advanced/Display/TFT_Terminal/TFT_Terminal.ino (Terminal/ Serial communication)
https://github.com/m5stack/M5Stack/blob/master/examples/Basics/Display/Display.ino (Display)
https://github.com/m5stack/FACES-Firmware/blob/master/KeyBoard.ino (Keyboard)
https://github.com/Bodmer/TFT_eSPI (Display features)

Source of original guide (Yama-chan):
https://www.youtube.com/watch?v=uOhBxapBLj4

My Video:
https://www.youtube.com/shorts/rUBs_ZbnMLE

What you'll need:
https://shop.m5stack.com/products/face?variant=17290437623898
https://www.raspberrypi.com/products/raspberry-pi-zero/ or https://www.raspberrypi.com/products/raspberry-pi-zero-w/
https://shop.m5stack.com/products/proto-module?variant=16804775198810
-A soldering iron + solder
-Wire
-Electrical tape or some other form of sticking down the raspberry pi

About Yama-chan's guide:
The guide included wiring diagrams and snippets of code that were used in this project, hence the credit, however yama-chan lost the
original full source code and therefore this meant many people looking to be able to do this were unable to without writing their own code
which some would be unable to do. 
I decided to write the code myself and after looking over the snippets included in yama-chan's video, M5Stack example codes and figuring out
how serial communication works, after 4 days of on and off coding, trial and error and bug squishing I was finally able to produce code that
produces similar results as to that in yama-chan's video.

Steps:
(very similar to Yama-chan's video except my version of the code is uploaded instead of the code mentioned in the video)

-Unscrew the chassis of the prototype module and set it aside
-Identify the orienation of the pins on the prototype board (I reccommend having the board green side up with the gpio ports on the left)
-Identify the orientation of the raspberry pi (I reccomment having the board sd card side down with the gpio pins on the left)
-Find the 5v, GND, pin 16 and pin 17 pins on the prototype board
-Solder colour coded thin wire to them (a source of good cheap wire I use is from a repurposed HDMI cable, you'll get loads of long thin wire)
-Thread the wire through to the other side of the board (as in the pictures below)
-Thread them out the top you soldered onto
-Cut excess wire, leaving only about 1cm of each wire sticking out
-Solder the 5v wire to the 5v pin on the Raspberry Pi's gpio port, GND to GND, M5Stack 16 to RPi GPIO 14 and M5Stack 17 to RPi GPIO 15 (as in Yama-chan's video)
-Flip the raspberry pi over and use whatever method you'd like to stick it to the prototype board(I used electrical tape to get a solid stick and no shorting)
-Flash rasbian onto the Raspberry Pi's sd card (I will include the appropriate version)
-Modify the config.txt and cmdline.txt files found in the boot partition that shows up on the sd card (I will include pictures)
-Use Arduino IDE to flash the M5StackRPi.ino file to the M5Stack
-You should be done!
PLEASE NOTE that I am extremely new to C++ and therefore the code will not be as clean or as bug-free as you may expect, I learned the majority
of my C++ knowledge over the course of the past few days working on this project so results may not be as pristine as expected.

Identified bugs:
-If the M5Stack is restarted without being fully powered off the Raspberry Pi remains powered on and the previously displayed text will not be
displayed but new text can still be inputted and outputted.
-As of now I have found no way to delete characters, meaning there is no option to backspace, if you make an error your best option is press enter
and retype.
-There is quite alot of screen tearing when alot of text is being scrolled through at high speeds, particularly when the Raspberry Pi is booting up,
I believe this is a hardware issue and probably cannot be fixed but further tinkering will confirm or deny this.

Included in the code i have added the option to assign custom commands to the three buttons on the M5Stack, The first two being the default pi login
details to speed up logging in, and the third being the reboot command. (A= pi, B= raspberry, C= sudo reboot) These commands can be changed to suit
whatever needs you may have.


![20220218_212145](https://user-images.githubusercontent.com/61987723/154763051-81be25ae-e026-4ffa-b7c3-b98ae51bdc33.jpg)
The finished product

![20220218_203458](https://user-images.githubusercontent.com/61987723/154763118-642bedb1-31cd-4c00-9ef9-e5ce7add5312.jpg)
![20220214_210007](https://user-images.githubusercontent.com/61987723/154763138-4bcacc8f-bcc6-4815-9fcd-f1aaed739dde.jpg)
Wiring, I suggest you do something similar when wiring up your own so as to prevent wires being damaged


![gpiopinsv3withpi](https://user-images.githubusercontent.com/61987723/154765700-0bad4017-3975-4694-b438-6a9d1a743d57.png)
RPi GPIO pinout

![1584654528449-m-gpio](https://user-images.githubusercontent.com/61987723/154765763-8d1b805f-4202-44ab-8c88-993ad93f13d2.png)
M5Stack GPIO pinout


