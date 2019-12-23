# fbtft---SSD1322
SSD1322 driver for fbtft
 
 Not Tested 
 
1. Copy this file to "/linux-mainline/linux-5.4.y/drivers/staging/fbtft"
     "cd /.../linux-mainline/linux-5.4.y/drivers/staging/fbtft"
     "wget https://raw.githubusercontent.com/MarkoBursic/fbtft---SSD1322/master/fb_ssd1322.c"
2. Add following text to "fbtft/Kconfig"</br>
      config FB_TFT_SSD1322</br>
        tristate "FB driver for the SSD1322 OLED Controller"</br>
        depends on FB_TFT</br>
        help</br>
          Framebuffer support for SSD1322</br>
3. Add "obj-$(CONFIG_FB_TFT_SSD1322)     += fb_ssd1322.o" to "fbtft/Makefile"
4. Add files to git : 
     "add git fb_ssd1322.c"
     "add git Makefife"
     "add git Kconfig"
5. "git commit -s -v"
6. "git format-patch -1 HEAD"
7. copy patch to userpatch directory (valid for Armbian), for example /userpatches/kernel/rockchip64-current
4. Enable the specific driver to be compiled, mark as M</br>
>Device Drivers ---></br>
>>Staging drivers ---></br>
>>>Support for small TFT LCD display modules ---></br>
>>>>FB driver for the SSD1322 OLED Controller</br>
5. Compile the kernel and install modules after compiled.
6. sudo modprobe fb_ssd1322
7. sudo modprobe fbtft_device custom name=fb_ssd1322 width=256 height=64 speed=16000000 gpios=dc:23,reset:24
8. use fbtest to test OLED
