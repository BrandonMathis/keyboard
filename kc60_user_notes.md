# KC60 Keyboard end-user tips, tricks, programming notes, etc. #

## Useful URLs ##

Original product drop - <br />
[https://www.massdrop.com/buy/kc60-mechanical-keyboard](https://www.massdrop.com/buy/kc60-mechanical-keyboard) <br />
Configurator web page - [http://123.57.250.164:9128/](http://123.57.250.164:9128/)<br /><br />

Flashing information - <br />
[https://www.keychatter.com/2015/07/05/programming-the-kc60/](https://www.keychatter.com/2015/07/05/programming-the-kc60/)<br />
[https://github.com/tmk/tmk_keyboard](https://github.com/tmk/tmk_keyboard)<br />
[https://geekhack.org/index.php](https://geekhack.org/index.php)<br />
[https://github.com/kairyu/tkg-toolkit](https://github.com/kairyu/tkg-toolkit)<br />

Reviews - <br />
livingspeedbump - [https://www.keychatter.com/2015/07/01/review-kc60-3/](https://www.keychatter.com/2015/07/01/review-kc60-3/)<br />

USB cable sources -
* http://pexonpcs.co.uk/
* http://www.mimic-cables.com/
* http://zealpc.net/
* http://sentrantpc.com/
* http://www.reddit.com/r/mechmarket/comments/35npeg/wts_sleeved_usb_cables_new_colors/

Other useful links -
* /r/MechanicalKeyboards: https://www.reddit.com/r/MechanicalKeyboards/
* Keyboard mapping software: https://sharpkeys.codeplex.com
* Custom layout designer https://www.trulyergonomic.com/store/layout-designer--configurator--reprogrammable--truly-ergonomic-mechanical-keyboard/
* Massdrop for Cherry MX switch tester https://www.massdrop.com/buy/cm-storm-cherry-mx-switch-tester
* Massdrop for bluetooth adapter https://www.massdrop.com/buy/bluetooth-keyboard-adapter
* Easy AVR Firmware http://deskthority.net/wiki/Easy_AVR_USB_Keyboard_Firmware
* How to remove switch tops https://www.keychatter.com/2015/07/06/guide-removing-switch-tops-on-the-kc60/
* LED install guide https://www.keychatter.com/2015/07/10/guide-adding-leds-to-the-kc60/
* URL from keyboard badge http://www.robowaishe.com
* Keychatter KC60 Guide list https://www.keychatter.com/?s=kc60

## First drop purchase options ##

##### Switch Types #####
* Cherry MX Black (+$7 USD)
* Cherry MX Blue (+$15 USD)
* Cherry MX Brown (+$15 USD)
* Cherry MX Clear (+$20 USD)
* Cherry MX Green (+$20 USD)
* Cherry MX Red (+$15 USD)
* Gateron Black
* Gateron Blue
* Gateron Brown
* Gateron Clear
* Gateron Red
* Gateron Yellow

##### Case Colors #####
* Black
* White

##### Keycap choices #####
* PBT with Purple Dye Sublimated (+$15 USD)
* PBT Black with Laser Engraved Legends
* PBT White with Laser Engraved Legends

##### LED options #####
* No LED
* White LEDs

## Technical Specs ##

**Manufacturer:** NPKC<br />
**Compatibility:** Linux, Mac OS X, Windows<br />
**USB:** Mini, detachable cable<br />
**Size:** 11.3 x 4.1 x 1.3 in (288. x 104.6 x 33.3 mm)<br />

**Notes:**
* Compatible with *most* 60% base plates, including Pok3r cases.
* Built with ATmega32u microcontroller
* 9 layers including base layer, 8 programmable layers
* 6 key roll over (6KRO)
* Supports media controls
* LEDs can dim, but are not individually addressable
* Caps Lock LED is dedicated and reflects caps lock status
* Original shipping date August 12, 2015
* First 90 shipment week of September 7, 2015
* Micro USB connector, comes with ~6' (2m) cable
* Button on bottom is for keyboard reset/flashing

## User notes from Massdrop Discussion ##

The programming guide is linked below, but it doesn't mention anything about the Fn layer options. You can infer the functionality on a few entries in the drop down menu based on the options offered to the right, and the default layout:
Layer 0 Fn (function #2 in drop down) should be enable Fn layer 1 while pressed down.
Layer 1 Fn (function #3 in drop down) should be to enable Fn layer 2 once pressed (and released).
Layer 2 Fn (function #4 in drop down) I'm not 100% sure about, but since 2 is selected I imagine it means removing Fn layer 2 and going back to the previous layer.
The last entry is macro. The few entries with Ctrl/Shift/Alt/Win options shouldn't be hard to figure out by trial and error. The ones without options I'd be careful about.
https://www.keychatter.com/2015/07/05/programming-the-kc60/

----------

Decided to just run it through Google translate:
空操作	-	No operation
瞬时开启层	-	Instantaneous open layer
开启层	-	Open layer
关闭层	-	Close Layer
开关层	-	Switch layer
瞬时开启、 按键	-	Momentary open , button
修饰键	-	Modifier keys
组合键	-	Key combination
单击修饰键	-	Click modifier keys
开关修饰键	-	Switch modifier keys
清除层状态	-	Clear layer status
宏	-	Macros

----------

Anyone who is having problems flashing and is getting the "did you remember to press the reset button?" message: it's simply a matter of holding the button down for a very long time. It takes about a full minute of holding the reset button before the chip restarts. Just keep holding even after the error message comes up, and eventually it will flash! Good luck and have fun!

----------

I start holding it before the "did you forget..." prompt, and continue holding it for a bit after. If it still doesn't work, you may need to install some drivers. Go into the "tkg-toolkit-master\windows\tool" folder, and run zadig_2.1.2.exe. Once it comes up, hold down the reset button until the chip restarts. This could take up to a minute, and you'll know it happens, because the leds suddenly dim. At this point "ATm32U4DFU" will suddenly appear in the drop down box. When that happens, click "install WCID driver" and it will install the USB driver for the atmel chip. After that, restart your computer just to be safe, then attempt to flash the firmware. (drag drop the .hex file onto reflash.bat, hit 'y'es, then immediately hold down the reset button until you see the firmware install script running, which could take up to 60 seconds)

----------

This worked for me. Opened zadig, held down the reset button for what felt like a very long time (I was starting to doubt) and then it recognized the board and I clicked "Install driver".
I restarted my computer and the board did not work initially (don't panic) but I made it to dropping the hex file onto and it loaded the firmware right after I entered [y]es, so my guess why the board wasn't working is because it was still in bootloader mode.
Main takeaway is that you really do have to press and hold and hold and hold the reset button.

----------

That worked for me thank you so much. For anyone else when opening zadig hold and release the reset button until you see one device found. Proceed to restart your PC after installing the drivers. Now the scary part, when I dropped the new HEX file in the reflash.bat I still got the error "did you remember to press the reset button?" DONT WORRY! just push the reset button down once again and the firmware will update. Hope this helps for others.

----------

I haven't figured out the "No" button yet, but it seems to me like the pressing a layer function key "adds" the layer on top of your current layer, erasing only keys that have been assigned. To get to additional layers, you can press the first fn key (mine is mapped to caps lock option 3 "open layer", and goes to layer 1). Then map an additional key on that layer to go to the next layer. Make sure you have a key set to "clear layers" on every layer other than 0, or you can get stuck! I like to use escape for this purpose.
For your colemak example, you can map caps lock to the "open layer" option, and go to layer 1. Then on the layer 1 page, map escape to "clear layers", and map capslock to "open layer", and set it to go to layer 2. This would be your colemak layer, and would also need a clear layers key. To get to it, you would simply tap capslock twice. To go back, hit escape once from either layer.
Another useful function is the sixth one down, with the comma. This will switch to a layer only as long as the button is held down. For example: I have capslock set to open layer 1. This contains a variety of vim-style key bindings like d being mapped to delete. I then have shift on layer 1 set to move to layer 2, only when it's held down. So if I'm in "vim mode", I can hit shift so that D will now delete the whole line instead of just a character.
Has anyone figured out how to get the "start" key into macros yet? I'd like to have a key to open notepad, but I need Start+R in the macro, and the interface won't snag that key for some reason. It also won't let you type out a macro and copy-paste it in, so I can't make an alt-F4 macro either.

----------

When 'Unknown Device #1' appears is when you want to start instaling the drivers. Once you complete the driver install the reflash.bat file should work.

----------

Aright guys, here is how to reprogram the KC60 on a Mac:
NOTE: Massdrop's online comments system automatically parses the text and moves all URLs to the bottom of the post. There are a few files that you will need to use that end in ".sh". The parser thinks that this is a URL, and it is removing all refrences to .sh files. In order to get around this I have placed a space before ".sh". The same holds true for the ".hex" extension.
You will need to manually remove the space when you attempt to run the following commands!
1. Download the TKG-Toolk from Github (click on download zip on the right).
2. Unzip the folder and go into the "Linux" folder.
3. Go into the "bin" folder.
4. The supplied "jq" file is a JSON parser, but it was compiled for Linux. Because of this it will not work on a Mac. You can Download the Mac version of jq and replace the linux version in the bin folder. You can get it from jq's Github page (link listed below). Download the version that best suits your OSX, if you are on an older version, like Snow Leopoard then you should download the oldest Mac version.
5. Exit the "bin" folder and return to the "Linux" Folder
6. Open the file called "reflash .sh" in a text editor.
7. There is a bug within the reflash script where the variables are not being parsed correctly from the config file. The original code is using declare with the -g flag to create the variables. But bash doesn't have the -g flag for declare.
Go to line 43, or search for the word "declare". Replace this line with:
eval "$line"
8. You now need to install the dfu-programmer, you can do this via Homebrew. If you don't have Homebrew installed you can get it by following the instructions at Homebrew's site. (Link listed below)
Press command + space to open up Spotlight and search for "Terminal". Open Terminal and input the following:
brew install dfu-programmer
9. Place the .hex file from the online configurator into the "Linux" folder.
10. You need to point your terminal to the "Linux" folder. Here is the easiest way to do that:
Type "cd " into the terminal, those are the letters cd and a space. Now drag and drop the "Linux" folder into Terminal. The path to the "Linux" folder should now be autofilled.
Press Enter. You should now be in the folder.
11. You need to set the permissions of the scripts so that they can be executed. If you skip this step the scripts can not run. Input these commands one at a time. Make sure you do this from within the "Linux" folder.
Remember to remove the spaces before .sh!
chmod +x reflash .sh
chmod +x setup .sh
chmod +x bin/jq
12. Run the setup script. Input the following into your Terminal:
./setup .sh
13. Select GHPad -> Default Firmware -> atmel_dfu Bootloader
14. Run the reflash script:
Remember to remove the space before .hex!
./reflash kc60 .hex
Note: Replace "kc60 .hex" with the name of you hex file if it has a different name.
15. Press "y" when it asks you if you want to continue.
16. Flip over the keyboard and press the reset button when you see the message "Wating for Bootloader...".
If everything works out you should get a "Success!" message.
https://github.com/kairyu/tkg-toolkit
https://stedolan.github.io/jq/download/
http://brew.sh/

---------

I see, looks like I forgot a step.
Go to the jq site and download the OSX binary. Unzip it, the file will be named "jq-osx-x86_64"
or something similar. Go to the "bin" folder and delete the original jq file and replace it with the file you downloaded. Now rename the file from "jq-osx-x86_64" to "jq".
It should now work if you follow the rest of the steps, specifically the one about setting permissions.
https://stedolan.github.io/jq/download/

----------

If you are still having problems with jq you can just skip this step, along with the setup script steps. The only thing the setup script does is create a file that contains some info about which settings you want the reflash script to use. Fixing these issues will allow you to program other keyboards, but if you are only ever going to use this for the KC60 you can simply go into a text editor and paste the following:
Name=GHPad
MCU=atmega32u4
Firmware=ghpad.hex
Bootloader=atmel_dfu
Then save this file in the "conf" folder and name it "default.ini". It should work if you complete the rest of the instructions.

----------

Since the KC60 is using TMK for it's firmware, the following document will shed some light as to what the different function modes in the configurator do. Scroll down to "3. Layer switching Example".
Right now I have settled on this pretty cool setup: Tapping f uses the key as normal, but holding f takes me to go to another layer which has vim style arrow keys (hjkl) and the number keys mimic the mac keyboard's media keys. If I hold d while holding f it will take me to another layer which gives me the standard function keys.
https://github.com/tmk/tmk_keyboard/blob/master/doc/keymap.md

----------

KC60 does use TMK, and I also found the code of its online programmer. Hopefully Massdrop @AlexPeterkin can request the developer to release the files under tmk_keyboard/keyboard/kc60 so we can do a lot with this keyboard!!!

https://github.com/jichuntao/online_compiler

---------

to whom want do advanced reprogramming of this keyboard, you should check this fork of tmk_keyboard on github. Pretty everything you need for this hardware are there and you could even write your own keyboard firmware based on this one.

https://github.com/jichuntao/tmk_keyboard

----------

Tried and managed to flash a new layout. Some notes:
- In the web tool, after clicking the blue Save button, the URL in the address bar changes and now contains a representation of your layout. You can bookmark it and resume editing at a later time.
- At the "waiting for Bootloader" stage I found that I only had to press the button for about 5 seconds and release it, then the flashing started.
- If you flash under OSX, you can use homebrew to install jq, and modify setup.sh to point to it: JQ=/usr/local/bin/jq



### Acknowledgements ###
Information on this page was gathered from the many postings to Massdrop, Reddit, GIT, and other sources. Thanks go to all the original publishers including (but not limited to):

AlexPeterkin, asphodel, Frostbyte, hjc1710, livingspeedbump, Makami, NanoGEEK, Nickajeglin, Regus, ruiwui, vppl

If I forgot someone please accept my apologies and add yourself to the list, or send me a note.