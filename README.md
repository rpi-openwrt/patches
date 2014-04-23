Patches
=======

Patches against OpenWRT trunk and package feed to enable building properly for rpi target with rpi packages.

Patch patches from base-system folder against trunk and then patches from packages folder against your local packages tree that you can obtain by commanding follwing in the trunk's root tree:<br/>
<pre>
/usr/src/openwrt/trunk $ ./scripts/feeds update -a
</pre>
This updates all package feeds (this doesn't yet enable the package tree), if you want to only update packages feed and no other feeds:<br/>
<pre>
/usr/src/openwrt/trunk $ ./script/feeds update -p packages
</pre>
 
Guide to patching against openwrt trunk
=======================================
Download contents of this repository to your trunk tree (so it's in trunk/patches), you can do this by changing directory to your trunk directory and entering following command:<br/>
<pre>
/usr/src/openwrt/trunk $ git clone https://github.com/rpi-openwrt/patches.git
</pre>

Then go to your trunk directory.. Mine is /usr/src/openwrt/trunk<br/>
And execute following commands:<br/>
<pre>
/usr/src/openwrt/trunk $ patch -p1 &lt; patches/base-system/openwrt-populatefs-fixed.patch
/usr/src/openwrt/trunk $ patch -p1 &lt; patches/base-system/xorg-macros-upgrade.patch
/usr/src/openwrt/trunk $ patch -p1 &lt; patches/base-system/udev-add-hostbuild.patch
/usr/src/openwrt/trunk $ patch -p1 &lt; patches/base-system/lua-add-fpic.patch
/usr/src/openwrt/trunk $ patch -p1 &lt; patches/base-system/add_rpi_feed.patch
</pre>

Guide to patching against packages tree
=======================================
First patch your openwrt trunk, you should have now remaining patches in trunk/patches.<br/>
Go to your trunk directory, mine is /usr/src/openwrt/trunk<br/>
Obtain atleast packages tree (check the top of the documentation for guidance when needed..)<br/>
And execute following commands:<br/>
<pre>
/usr/src/openwrt/trunk $ cd feeds/packages
/usr/src/openwrt/trunk/feeds/packages $ patch -p1 &lt; ../../patches/packages/diffutils.patch
/usr/src/openwrt/trunk/feeds/packages $ patch -p1 &lt; ../../patches/packages/dialog-v2.patch
/usr/src/openwrt/trunk/feeds/packages $ patch -p1 &lt; ../../patches/packages/dbus.patch
</pre>

What next?
==========
Follow guidance on the Readme of package rpi package repository for success:
https://github.com/rpi-openwrt/rpi-packages

About
=====
These patches are also available from the OpenWrt trac and some are duplicated to the mailing list as well.
Only patch add_rpi_feed.patch is not available from other sources mentioned here.
