Patches
=======

Patches against OpenWRT trunk and package feed to enable building properly for rpi target with rpi packages.

Patch patches from base-system folder against trunk and then patches from packages folder against your local packages tree that you can obtain by commanding follwing in the trunk's root tree:
 ./scripts/feeds update -a
or
 ./script/feeds update -p packages
 
Guide to patching against openwrt trunk
=======================================
Download contents of this repository to your trunk tree (so it's in trunk/patches)
Then go to your trunk directory.. Mine is /usr/src/openwrt/trunk
And execute following commands:
/usr/src/openwrt/trunk $ patch -p1 < patches/base-system/openwrt-populatefs-fixed.patch
/usr/src/openwrt/trunk $ patch -p1 < patches/base-system/xorg-macros-upgrade.patch
/usr/src/openwrt/trunk $ patch -p1 < patches/base-system/udev-add-hostbuild.patch
/usr/src/openwrt/trunk $ patch -p1 < patches/base-system/lua-add-fpic.patch
/usr/src/openwrt/trunk $ patch -p1 < patches/base-system/add_rpi_feed.patch

Guide to patching against packages tree
=======================================
First patch your openwrt trunk, you should have now remaining patches in trunk/patches.
Go to your trunk directory, mine is /usr/src/openwrt/trunk
Obtain atleast packages tree (check the top of the documentation for guidance when needed..)
And execute following commands:
/usr/src/openwrt/trunk $ cd feeds/packages
/usr/src/openwrt/trunk/feeds/packages $ patch -p1 < ../../patches/packages/diffutils.patch
/usr/src/openwrt/trunk/feeds/packages $ patch -p1 < ../../patches/packages/dialog-v2.patch
/usr/src/openwrt/trunk/feeds/packages $ patch -p1 < ../../patches/packages/dbus.patch

What next?
==========
Follow guidance on the Readme of package rpi package repository for success:
https://github.com/rpi-openwrt/rpi-packages

About
=====
These patches are also available from the OpenWrt trac and some are duplicated to the mailing list as well.
Only patch add_rpi_feed.patch is not available from other sources mentioned here.
