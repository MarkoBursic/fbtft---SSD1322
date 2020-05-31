# fbtft---SSD1322
SSD1322 driver for fbtft
Generation of .patch for the linux kernel -> device drivers -> staging -> fbtft

Tested with Armbian (Debian) Buster 10, Linux 5.4.38-rockchip64 on Rockpi 4B (RK3399 SoC)
Display: ER-OLED032-1  - BuyDisplay.com
 
1. Copy this file to "/linux-mainline/linux-5.4.y/drivers/staging/fbtft"</br>
     "cd /.../linux-mainline/linux-5.4.y/drivers/staging/fbtft"</br>
     "wget https://raw.githubusercontent.com/MarkoBursic/fbtft---SSD1322/master/fb_ssd1322.c"</br>
2. Add following text to "fbtft/Kconfig"</br>
      config FB_TFT_SSD1322</br>
        tristate "FB driver for the SSD1322 OLED Controller"</br>
        depends on FB_TFT</br>
        help</br>
          Framebuffer support for SSD1322</br>
3. Add "obj-$(CONFIG_FB_TFT_SSD1322)     += fb_ssd1322.o" to "fbtft/Makefile"
4. Add files to git : </br>
     "git add /..../drivers/staging/fbtft/fb_ssd1322.c"</br>
     "git add /..../drivers/staging/fbtft/Makefife"</br>
     "git add /..../drivers/staging/fbtft/Kconfig"</br>
5. git config --global user.email "you@example.com"</br>
                      OR</br>
   git config --global user.name "Your Name"</br>
5. "git commit -s -v"</br>
remove comment line # o those three files, save and exit

6. "git format-patch -1 HEAD"
7. copy patch to userpatch directory (valid for Armbian), for example /userpatches/kernel/rockchip64-current
8. Enable the specific driver to be compiled, mark as M</br>
>Device Drivers ---></br>
>>Staging drivers ---></br>
>>>Support for small TFT LCD display modules ---></br>
>>>>FB driver for the SSD1322 OLED Controller</br>
9. Compile the kernel and install modules after compiled.
10. sudo modprobe fb_ssd1322
11. sudo modprobe fbtft_device custom name=fb_ssd1322 width=256 height=64 speed=16000000 gpios=dc:23,reset:24
12. use fbtest to test OLED

Alternative:
use .patch file: wget https://raw.githubusercontent.com/MarkoBursic/fbtft---SSD1322/master/0001-Signed-off-by-root-marko.bursic73-gmail.com.patch
