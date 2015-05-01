This is a current AOSP build with minimal changes needed for our good old HTC Desire (BRAVO).

Original BRAVO sources are from http://evervolv.com.

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
- do a repo init: "repo init -u https://github.com/justremotephone/platform_manifest.git -b android-5.0-bravo"
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
