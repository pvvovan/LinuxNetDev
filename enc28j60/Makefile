ifneq ($(KERNELRELEASE),) # kbuild part of makefile
CFLAGS_enc28j60.o := -DDEBUG
obj-m := enc28j60.o
else # normal makefile
KDIR ?= /home/vovan/Desktop/uboot-x15/vanilla/linux-stable
#KDIR ?= /lib/modddules/$(shell uname -r)/build

default: module app
module:
	$(MAKE) -C $(KDIR) M=$(PWD) C=1 modules
clean:
	$(MAKE) -C $(KDIR) M=$(PWD) C=1 clean
	rm -f lus-app

#CC = $(CROSS_COMPILE)gcc
CC = /opt/gcc-linaro-7.3.1-2018.05-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf-gcc
CFLAGS = -O2 -Wall -Werror

app:
	$(CC) $(CFLAGS) lus-app.c -o lus-app

.PHONY: module clean app
endif
