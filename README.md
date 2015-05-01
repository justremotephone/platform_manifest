This is a current AOSP build with minimal changes needed for our good old HTC Desire (BRAVO).

Original BRAVO sources are from http://evervolv.com.

This branch uses a newer 3.0 kernel!
 
Many thanks to nikez for his original work on the 3.0 kernel:
https://github.com/nikez/android_kernel_htc_qsd8k

Also many thanks to spezi77 which has provided me with newer commits at:
https://github.com/spezi77/android_kernel_htc_qsd8k_3.0.x/commits/3.0-base

I have fixed some USB connection, radio data and some stability issues. But still further work is needed. Especially standby power consumption is too height. I have invested some time for that power problem but I have not found a solution so far.

The minimal change set should allow fast rebases on top of future android releases.

Following works:

- WIFI
- BLUETOOTH
- RADIO (may need some time after reboot to connect)
- ....

Not working:

- Camera
- Multimedia codecs

WARNING: Because of limited internal storage of the HTC Desire this build needs an external SD-CARD partition as internal data partition.

To use the internal data partition revert commit: https://github.com/justremotephone/android_device_htc_bravo/commit/df861492d0ce2162d897a3bb4c0cef6abac091fd

Build and installation:

- setup a build environment: https://source.android.com/source/downloading.html
- do a repo init: "repo init -u https://github.com/justremotephone/platform_manifest.git -b android-5.1-bravo-30"
- do a repo sync
- lunch ev_bravo-eng
- "make -j9 bootimage"
- "make -j9 systemimage"
- fastboot flash boot boot.img
- fastboot flash system system.img
- fastboot erase cache
- use a recovery tool to create a fresh formatted ext-partition on your sd card
- reboot
- ...
