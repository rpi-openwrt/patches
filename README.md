patches
=======

Patches against OpenWRT trunk and package feed to enable building properly for rpi target with rpi packages.

Patch patches from base-system folder against trunk and then patches from packages folder against your local packages tree that you can obtain by commanding follwing in the trunk's root tree:
 ./scripts/feeds update -a
or
 ./script/feeds update -p packages
 

About
=====
These patches are also available from the OpenWrt trac and some are duplicated to the mailing list as well.
Only patch add_rpi_feed.patch is not available from other sources mentioned here.
