---
title: Factory Images for Nexus and Pixel Devices
date: 2019-10-18 10:36:16
categories:
- Flash ROM
---

This page contains binary image files that allow you to restore your Nexus or Pixel device's original factory firmware. You will find these files useful if you have flashed custom builds on your device, and wish to return your device to its factory state.

Note that it's typically easier and safer to sideload the [full OTA image](https://developers.google.com/android/ota) instead.

If you do use a factory image, please make sure that you re-lock your bootloader when the process is complete.

These files are for use only on your personal Nexus or Pixel devices and may not be disassembled, decompiled, reverse engineered, modified or redistributed by you or used in any way except as specifically set forth in the license terms that came with your device.

### Terms and conditions
> ***Warning***: Installing a factory image will erase all data from the device, and unlocking the bootloader will make your device less secure. In most cases it should be possible to sideload the full OTA image instead. This does not require a data wipe, and does not require the bootloader to be unlocked.

While it may be possible to restore certain data backed up to your Google Account, apps and their associated data will be uninstalled. Before proceeding, please ensure that data you would like to retain is [backed up to your Google Account](https://support.google.com/nexus/answer/2819582#backup).

Downloading of the system image and use of the device software is subject to the [Google Terms of Service](https://www.google.com/intl/en/policies/terms/). By continuing, you agree to the [Google Terms of Service](https://www.google.com/intl/en/policies/terms/) and [Privacy Policy](https://www.google.com/intl/en/policies/privacy/). Your downloading of the system image and use of the device software may also be subject to certain third-party terms of service, which can be found in Settings > About phone > Legal information, or as otherwise provided.

### Flashing instructions
The factory image downloaded from this page includes a script that flashes the device, typically named `flash-all.sh` (On Windows systems, use `flash-all.bat` instead).

> ***Warning***: To flash a device using one of the system images below (or one of your own), you also need the latest fastboot tool. You can get it from the Android SDK Platform-Tools package, which you can [download here](https://developer.android.com/studio/releases/platform-tools.html).

Once you have the `fastboot` tool, add it to your `PATH` environment variable (the `flash-all` script below must be able to find it).

Also be certain that you've set up USB access for your device, as described in Run Apps on a Hardware Device.

> ***Caution:*** Flashing a new system image deletes all user data. Be certain to first backup any personal data such as photos.

#### To flash a system image:

1. Download the appropriate system image for your device below, then unzip it to a safe directory.
2. Connect your device to your computer over USB.
3. Start the device in fastboot mode with one of the following methods:
  - Using the [adb tool](http://developer.android.com/tools/help/adb.html): With the device powered on, execute:
    > adb reboot bootloader

  - Using a key combo: Turn the device off, then turn it on and immediately hold down the relevant [key combination](https://source.android.com/source/running#booting-into-fastboot-mode) for your device.

4. If necessary, unlock the device's bootloader using one of the following methods:

  - If you are updating a Nexus or Pixel device that is manufactured in 2015 or later (for example, a Nexus 5X, Nexus 6P, Pixel, Pixel XL, Pixel 2 or Pixel 2 XL device), run this command:
    > fastboot flashing unlock

  > ***Note***: the 'flashing unlock' command is only available with fastboot version 23.0.1 or later. The latest available version of fastboot can be downloaded from [SDK Platform Tools](https://developer.android.com/studio/releases/platform-tools.html).

  - For Pixel 2: To flash the bootloader, Pixel 2's boot loader must be updated to at least Oreo MR1's version first. This may be done by applying an over-the-air (OTA) update, or sideloading a [full OTA](https://developers.google.com/android/ota) with the instructions on that page.
  - For Pixel 2 _XL only_ with loader version prior to TMZ20a: the critical partitions may also need to be unlocked before flashing. The unlock can be performed with this command, and should NOT be done on other devices:
    > fastboot flashing unlock_critical

  - If you are updating an older device, run this command:
    > fastboot oem unlock

  The target device will show you a confirmation screen. (This erases all data on the target device.)

  See [Unlocking the bootloader](https://source.android.com/source/running#unlocking-the-bootloader) for more detailed instructions.

5. Open a terminal and navigate to the unzipped system image directory.
6. Execute the `flash-all` script. This script installs the necessary bootloader, baseband firmware(s), and operating system.

Once the script finishes, your device reboots. You should now lock the bootloader for security:

1. Start the device in fastboot mode again, as described above.

2. Execute:
  >fastboot flashing *lock*

  or, for older devices, run:
  >fastboot oem *lock*

Locking bootloader will wipe the data on some devices. After locking the bootloader, if you want to flash the device again, you must run `fastboot oem unlock` again, which will wipe the data.


<h2 id="bonito" is-upgraded="">"bonito" for Pixel 3a XL</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="bonitopd2a.190115.029">
    <td>9.0.0 (PD2A.190115.029, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bonito-pd2a.190115.029-factory-aac5b874.zip" class="gc-analytics-event" data-category="Android Images" data-label="bonito for Pixel 3a XL [PD2A.190115.029]">Link</a></td>
    <td>aac5b874226790cff9133ac62fef4724a05c00ab03ca988750eb712aed0bbc5e</td>
  </tr>
  <tr id="bonitopd2a.190115.032">
    <td>9.0.0 (PD2A.190115.032, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bonito-pd2a.190115.032-factory-18c01bb1.zip" class="gc-analytics-event" data-category="Android Images" data-label="bonito for Pixel 3a XL [PD2A.190115.032]">Link</a></td>
    <td>18c01bb19316442a8d5545155a163cbbf871b58d79313fe76f819fbca186e1fa</td>
  </tr>
  <tr id="bonitopq3b.190605.006">
    <td>9.0.0 (PQ3B.190605.006, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bonito-pq3b.190605.006-factory-8677ce70.zip" class="gc-analytics-event" data-category="Android Images" data-label="bonito for Pixel 3a XL [PQ3B.190605.006]">Link</a></td>
    <td>8677ce70e0b22160474d9363ce5e885e6340e86de3e5d7489a680fd5fc74bea8</td>
  </tr>
  <tr id="bonitopq3b.190705.003">
    <td>9.0.0 (PQ3B.190705.003, Jul 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bonito-pq3b.190705.003-factory-db56e533.zip" class="gc-analytics-event" data-category="Android Images" data-label="bonito for Pixel 3a XL [PQ3B.190705.003]">Link</a></td>
    <td>db56e533a61f949b5eb753fb9561c84e68147b868b7f75fb0330cfcc815169de</td>
  </tr>
  <tr id="bonitopq3b.190801.002">
    <td>9.0.0 (PQ3B.190801.002, Aug 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bonito-pq3b.190801.002-factory-61a2836d.zip" class="gc-analytics-event" data-category="Android Images" data-label="bonito for Pixel 3a XL [PQ3B.190801.002]">Link</a></td>
    <td>61a2836d098d640e0d7b79a4630f386f5e4d82a7d6a0e91289f141dab99541a5</td>
  </tr>
  <tr id="bonitoqp1a.190711.019">
    <td>10.0.0 (QP1A.190711.019, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bonito-qp1a.190711.019-factory-1c773c29.zip" class="gc-analytics-event" data-category="Android Images" data-label="bonito for Pixel 3a XL [QP1A.190711.019]">Link</a></td>
    <td>1c773c29c75a6ddb16216c3432f0755364332be55036ad760e93e9fe5fc50db1</td>
  </tr>
  <tr id="bonitoqp1a.190711.020">
    <td>10.0.0 (QP1A.190711.020, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bonito-qp1a.190711.020-factory-1f47c677.zip" class="gc-analytics-event" data-category="Android Images" data-label="bonito for Pixel 3a XL [QP1A.190711.020]">Link</a></td>
    <td>1f47c677bcb3ce427103a6388e3f07fb8a03789353cfd3baceb6c24e13b62f9a</td>
  </tr>
  <tr id="bonitoqp1a.190711.020.c3">
    <td>10.0.0 (QP1A.190711.020.C3, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bonito-qp1a.190711.020.c3-factory-ffac7a4a.zip" class="gc-analytics-event" data-category="Android Images" data-label="bonito for Pixel 3a XL [QP1A.190711.020.C3]">Link</a></td>
    <td>ffac7a4a1412546609f3dddffa6f83b5dc61ad424cf625b9c71429ddd2726cb6</td>
  </tr>
  <tr id="bonitoqp1a.191005.007">
    <td>10.0.0 (QP1A.191005.007, Oct 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bonito-qp1a.191005.007-factory-9754d7c6.zip" class="gc-analytics-event" data-category="Android Images" data-label="bonito for Pixel 3a XL [QP1A.191005.007]">Link</a></td>
    <td>9754d7c6c75199cc3c45eac5a9bf0ae685c3ce75e84b079e2a58af01b896e89a</td>
  </tr>
</tbody></table></div>

<h2 id="sargo" is-upgraded="">"sargo" for Pixel 3a</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="sargopd2a.190115.029">
    <td>9.0.0 (PD2A.190115.029, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sargo-pd2a.190115.029-factory-b05c97da.zip" class="gc-analytics-event" data-category="Android Images" data-label="sargo for Pixel 3a [PD2A.190115.029]">Link</a></td>
    <td>b05c97da93de98219c526c9cb59f4e9f5bcd0ab5daa7c8503ce0b44c1446b14e</td>
  </tr>
  <tr id="sargopd2a.190115.032">
    <td>9.0.0 (PD2A.190115.032, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sargo-pd2a.190115.032-factory-c0068fd4.zip" class="gc-analytics-event" data-category="Android Images" data-label="sargo for Pixel 3a [PD2A.190115.032]">Link</a></td>
    <td>c0068fd4b78c939cb9a84921f2c1fc15c5316618edaa9647c46387c58f24fe58</td>
  </tr>
  <tr id="sargopq3b.190605.006">
    <td>9.0.0 (PQ3B.190605.006, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sargo-pq3b.190605.006-factory-81f898b7.zip" class="gc-analytics-event" data-category="Android Images" data-label="sargo for Pixel 3a [PQ3B.190605.006]">Link</a></td>
    <td>81f898b7b792f1d25a1245922e130f0933d9937be3f3fcd2e089894c321ef3e6</td>
  </tr>
  <tr id="sargopq3b.190705.003">
    <td>9.0.0 (PQ3B.190705.003, Jul 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sargo-pq3b.190705.003-factory-55d7c2c4.zip" class="gc-analytics-event" data-category="Android Images" data-label="sargo for Pixel 3a [PQ3B.190705.003]">Link</a></td>
    <td>55d7c2c4445b698051ab12af5966789a94b2deb8aff8f596b5a16484016e38d7</td>
  </tr>
  <tr id="sargopq3b.190801.002">
    <td>9.0.0 (PQ3B.190801.002, Aug 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sargo-pq3b.190801.002-factory-56817dc2.zip" class="gc-analytics-event" data-category="Android Images" data-label="sargo for Pixel 3a [PQ3B.190801.002]">Link</a></td>
    <td>56817dc2993f0b3b6cf1972c74329ff154465849b8284731a27f8284a12fee5f</td>
  </tr>
  <tr id="sargoqp1a.190711.019">
    <td>10.0.0 (QP1A.190711.019, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sargo-qp1a.190711.019-factory-585217b6.zip" class="gc-analytics-event" data-category="Android Images" data-label="sargo for Pixel 3a [QP1A.190711.019]">Link</a></td>
    <td>585217b66b0f6b23bf03979d5853756d009ff45dd14750d754b90fc5d9109986</td>
  </tr>
  <tr id="sargoqp1a.190711.020">
    <td>10.0.0 (QP1A.190711.020, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sargo-qp1a.190711.020-factory-afb4dbc1.zip" class="gc-analytics-event" data-category="Android Images" data-label="sargo for Pixel 3a [QP1A.190711.020]">Link</a></td>
    <td>afb4dbc1df968aace547691a063a6bb6b2cc8cb6cc448b199a8b5b78803beb43</td>
  </tr>
  <tr id="sargoqp1a.190711.020.c3">
    <td>10.0.0 (QP1A.190711.020.C3, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sargo-qp1a.190711.020.c3-factory-2037b552.zip" class="gc-analytics-event" data-category="Android Images" data-label="sargo for Pixel 3a [QP1A.190711.020.C3]">Link</a></td>
    <td>2037b55299b85e6567c076172d4b19daf27d7d552ce497e6b4683769440896ed</td>
  </tr>
  <tr id="sargoqp1a.191005.007">
    <td>10.0.0 (QP1A.191005.007, Oct 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sargo-qp1a.191005.007-factory-664181b1.zip" class="gc-analytics-event" data-category="Android Images" data-label="sargo for Pixel 3a [QP1A.191005.007]">Link</a></td>
    <td>664181b1f02e42f177ca3cff0713f0c9f195a4b49b059649d0a5bb5677687b1a</td>
  </tr>
</tbody></table></div>

<h2 id="crosshatch" is-upgraded="">"crosshatch" for Pixel 3 XL</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="crosshatchpd1a.180720.030">
    <td>9.0.0 (PD1A.180720.030, Sep 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pd1a.180720.030-factory-38b1b90a.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PD1A.180720.030]">Link</a></td>
    <td>38b1b90a38dfd7f449cba4eb2cf786b76e39ee3d9b17cbc1ba6db6463545863e</td>
  </tr>
  <tr id="crosshatchpd1a.180720.031">
    <td>9.0.0 (PD1A.180720.031, Sep 2018, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pd1a.180720.031-factory-7e9da376.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PD1A.180720.031]">Link</a></td>
    <td>7e9da376a846c934eb3b4ca39833996ee453c3ad67bb23a365ba09862c286d03</td>
  </tr>
  <tr id="crosshatchpq1a.181105.017.a1">
    <td>9.0.0 (PQ1A.181105.017.A1, Nov 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq1a.181105.017.a1-factory-6f06f1a0.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ1A.181105.017.A1]">Link</a></td>
    <td>6f06f1a05e1fd18624a3f0b8d91ca0c38584ba77edc77ed2f2dd8e1651c61537</td>
  </tr>
  <tr id="crosshatchpq1a.181205.006">
    <td>9.0.0 (PQ1A.181205.006, Dec 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq1a.181205.006-factory-96b23504.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ1A.181205.006]">Link</a></td>
    <td>96b235048c53d3b37039c092889f1b8a749e9a407fea63659e0b3b90bd91c50e</td>
  </tr>
  <tr id="crosshatchpq1a.181205.006.a1">
    <td>9.0.0 (PQ1A.181205.006.A1, Dec 2018, Docomo)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq1a.181205.006.a1-factory-99bead33.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ1A.181205.006.A1]">Link</a></td>
    <td>99bead334525f4d26ef5777ebc910648674597e1322a2a95e9e2d4f9df5d69cf</td>
  </tr>
  <tr id="crosshatchpq1a.190105.004">
    <td>9.0.0 (PQ1A.190105.004, Jan 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq1a.190105.004-factory-7165155c.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ1A.190105.004]">Link</a></td>
    <td>7165155c738eac530a3d27bd03d166b3358065183627c41d4c4804a19a2795b0</td>
  </tr>
  <tr id="crosshatchpq2a.190205.001">
    <td>9.0.0 (PQ2A.190205.001, Feb 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq2a.190205.001-factory-b72bfd04.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ2A.190205.001]">Link</a></td>
    <td>b72bfd04a10ff6bd21de60f120242768851fc13a7cb404dd628c7fd4de23c5a2</td>
  </tr>
  <tr id="crosshatchpq2a.190305.002">
    <td>9.0.0 (PQ2A.190305.002, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq2a.190305.002-factory-dc7e9ca4.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ2A.190305.002]">Link</a></td>
    <td>dc7e9ca44a19fa2ce5a5ed54fc7be5f2f830006b4a0958842f90d5bc514ab91e</td>
  </tr>
  <tr id="crosshatchpq2a.190405.003">
    <td>9.0.0 (PQ2A.190405.003, Apr 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq2a.190405.003-factory-379f92bd.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ2A.190405.003]">Link</a></td>
    <td>379f92bd93a5cece17f5123ef6668099f71ddbc4add05f252bfe45f3066e7104</td>
  </tr>
  <tr id="crosshatchpq3a.190505.002">
    <td>9.0.0 (PQ3A.190505.002, May 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq3a.190505.002-factory-99879eba.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ3A.190505.002]">Link</a></td>
    <td>99879eba8020ad35c69a90f3b3d4443e857283d51deec33cd644da5c645e5f5a</td>
  </tr>
  <tr id="crosshatchpq3a.190605.003">
    <td>9.0.0 (PQ3A.190605.003, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq3a.190605.003-factory-3a0d8bba.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ3A.190605.003]">Link</a></td>
    <td>3a0d8bba48f542533edaf2fb135c23ef5133efbd709951627e85662752d7d569</td>
  </tr>
  <tr id="crosshatchpq3a.190605.004.a1">
    <td>9.0.0 (PQ3A.190605.004.A1, Jun 2019, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq3a.190605.004.a1-factory-0933f208.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ3A.190605.004.A1]">Link</a></td>
    <td>0933f2080c5bba78f2858c892ec899cda67c6c01373a25bbcae013fb906a7fc6</td>
  </tr>
  <tr id="crosshatchpq3a.190705.003">
    <td>9.0.0 (PQ3A.190705.003, Jul 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq3a.190705.003-factory-e59cf7a4.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ3A.190705.003]">Link</a></td>
    <td>e59cf7a412e48d0f78463a67dc0085d98b811026d7c593b8d61925c2d9895e02</td>
  </tr>
  <tr id="crosshatchpq3a.190801.002">
    <td>9.0.0 (PQ3A.190801.002, Aug 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-pq3a.190801.002-factory-15db810d.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [PQ3A.190801.002]">Link</a></td>
    <td>15db810de7d3aa3ad660ffe6bcd572178c8d7c3fa363fef308cde29e0225b6c1</td>
  </tr>
  <tr id="crosshatchqp1a.190711.019">
    <td>10.0.0 (QP1A.190711.019, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-qp1a.190711.019-factory-130c70be.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [QP1A.190711.019]">Link</a></td>
    <td>130c70bec13e24d0671f52fcc9ff4332b04011e7df9a8f53be42f13f9e02993e</td>
  </tr>
  <tr id="crosshatchqp1a.190711.020">
    <td>10.0.0 (QP1A.190711.020, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-qp1a.190711.020-factory-2eae0727.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [QP1A.190711.020]">Link</a></td>
    <td>2eae0727565dc516a60e05f8502671d24e6d4b25770618d83d8a763147e259d3</td>
  </tr>
  <tr id="crosshatchqp1a.190711.020.c3">
    <td>10.0.0 (QP1A.190711.020.C3, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-qp1a.190711.020.c3-factory-59b11ce9.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [QP1A.190711.020.C3]">Link</a></td>
    <td>59b11ce9a2cd8ef2f75fc3ebe6124924eade2a624d4e9bf516e82d16b9d79749</td>
  </tr>
  <tr id="crosshatchqp1a.191005.007">
    <td>10.0.0 (QP1A.191005.007, Oct 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/crosshatch-qp1a.191005.007-factory-2989a08d.zip" class="gc-analytics-event" data-category="Android Images" data-label="crosshatch for Pixel 3 XL [QP1A.191005.007]">Link</a></td>
    <td>2989a08d105bcbe12087d54054eb0c8a412ed220e1b4df06f93e33e0618e18fc</td>
  </tr>
</tbody></table></div>

<h2 id="blueline" is-upgraded="">"blueline" for Pixel 3</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="bluelinepd1a.180720.030">
    <td>9.0.0 (PD1A.180720.030, Sep 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pd1a.180720.030-factory-d6fefe86.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PD1A.180720.030]">Link</a></td>
    <td>d6fefe86e203d4c5b9f2559f82443fb883a34f82cf3a633a87bb342e2fd8bfca</td>
  </tr>
  <tr id="bluelinepd1a.180720.031">
    <td>9.0.0 (PD1A.180720.031, Sep 2018, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pd1a.180720.031-factory-3df41a2b.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PD1A.180720.031]">Link</a></td>
    <td>3df41a2b65335bb6c130f36b0bbd87c3f90822b7ef04f210232daacc3693142a</td>
  </tr>
  <tr id="bluelinepq1a.181105.017.a1">
    <td>9.0.0 (PQ1A.181105.017.A1, Nov 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq1a.181105.017.a1-factory-b00ec7b5.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ1A.181105.017.A1]">Link</a></td>
    <td>b00ec7b509c78ed06648e94ddb6fedcbac29a309d605cad11b55ace7865e2723</td>
  </tr>
  <tr id="bluelinepq1a.181205.006">
    <td>9.0.0 (PQ1A.181205.006, Dec 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq1a.181205.006-factory-af1829a6.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ1A.181205.006]">Link</a></td>
    <td>af1829a69d8c041729725a2dbd7033f12e4ef346f41353b8416bc25f6609e5cc</td>
  </tr>
  <tr id="bluelinepq1a.181205.006.a1">
    <td>9.0.0 (PQ1A.181205.006.A1, Dec 2018, Docomo)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq1a.181205.006.a1-factory-e0442d3b.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ1A.181205.006.A1]">Link</a></td>
    <td>e0442d3b0a9e5636f4979b5780b6173635fe73917e88ffe1b9d36c2bc45aa7bc</td>
  </tr>
  <tr id="bluelinepq1a.190105.004">
    <td>9.0.0 (PQ1A.190105.004, Jan 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq1a.190105.004-factory-49adfd52.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ1A.190105.004]">Link</a></td>
    <td>49adfd52b308b97c5bf576eea7e0ea8ba0f510866b5aea823e1cf1c8d93c3594</td>
  </tr>
  <tr id="bluelinepq2a.190205.001">
    <td>9.0.0 (PQ2A.190205.001, Feb 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq2a.190205.001-factory-7bb97f58.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ2A.190205.001]">Link</a></td>
    <td>7bb97f58ff9abbb6730da2ff6dea6ff938c936054d8d935ee27f412816cc21b8</td>
  </tr>
  <tr id="bluelinepq2a.190305.002">
    <td>9.0.0 (PQ2A.190305.002, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq2a.190305.002-factory-b8869812.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ2A.190305.002]">Link</a></td>
    <td>b8869812509521216f02bac1d24bf146e0fc11175dc79645b0a91b4029d7ddf8</td>
  </tr>
  <tr id="bluelinepq2a.190405.003">
    <td>9.0.0 (PQ2A.190405.003, Apr 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq2a.190405.003-factory-c12f40f0.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ2A.190405.003]">Link</a></td>
    <td>c12f40f0b189eb2daa80d029917bc9a8841da89cfcafa21b8f61b0d9f90826e7</td>
  </tr>
  <tr id="bluelinepq3a.190505.002">
    <td>9.0.0 (PQ3A.190505.002, May 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq3a.190505.002-factory-26d20025.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ3A.190505.002]">Link</a></td>
    <td>26d2002511d6a13fc523334b7f783dd757edd543179c7a5dc2f7e1d322efc6e3</td>
  </tr>
  <tr id="bluelinepq3a.190605.003">
    <td>9.0.0 (PQ3A.190605.003, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq3a.190605.003-factory-258494df.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ3A.190605.003]">Link</a></td>
    <td>258494df9d2bfb354f7afce3257369fb0b424a5dcd988b34d01b221ef1dc2caa</td>
  </tr>
  <tr id="bluelinepq3a.190605.004.a1">
    <td>9.0.0 (PQ3A.190605.004.A1, Jun 2019, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq3a.190605.004.a1-factory-da940910.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ3A.190605.004.A1]">Link</a></td>
    <td>da940910bf3ac99af6ae53be3971698737ba7cb86f42b4d19e67078fd19d7a58</td>
  </tr>
  <tr id="bluelinepq3a.190705.003">
    <td>9.0.0 (PQ3A.190705.003, Jul 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq3a.190705.003-factory-c14bfb79.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ3A.190705.003]">Link</a></td>
    <td>c14bfb79b6660398f0454279b98ab45ace896e115c462643c0685089f5f1758f</td>
  </tr>
  <tr id="bluelinepq3a.190801.002">
    <td>9.0.0 (PQ3A.190801.002, Aug 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-pq3a.190801.002-factory-f3d66c49.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [PQ3A.190801.002]">Link</a></td>
    <td>f3d66c498994c7ca8c63a97f74bbd2634db7f91e1e114e7924cb721a149ddd2b</td>
  </tr>
  <tr id="bluelineqp1a.190711.019">
    <td>10.0.0 (QP1A.190711.019, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-qp1a.190711.019-factory-434cc9b1.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [QP1A.190711.019]">Link</a></td>
    <td>434cc9b1e193aa337723a8a6961339c0046243e5a34cd74a1c44d31d9705cde8</td>
  </tr>
  <tr id="bluelineqp1a.190711.020">
    <td>10.0.0 (QP1A.190711.020, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-qp1a.190711.020-factory-b5633fdf.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [QP1A.190711.020]">Link</a></td>
    <td>b5633fdfa34df0fccc4b6dc86799b1a2ee6a2fc1de1cd9c8a08da7703ad81ec2</td>
  </tr>
  <tr id="bluelineqp1a.190711.020.c3">
    <td>10.0.0 (QP1A.190711.020.C3, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-qp1a.190711.020.c3-factory-1996b3cf.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [QP1A.190711.020.C3]">Link</a></td>
    <td>1996b3cfc4e83743127f356d349aef2bf577c96d9c8d109b9c8917c81125ab04</td>
  </tr>
  <tr id="bluelineqp1a.191005.007">
    <td>10.0.0 (QP1A.191005.007, Oct 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/blueline-qp1a.191005.007-factory-c36610c6.zip" class="gc-analytics-event" data-category="Android Images" data-label="blueline for Pixel 3 [QP1A.191005.007]">Link</a></td>
    <td>c36610c69c9561a53498836f3719b6d1b523496d6c9ffd48745b6b57d668b03a</td>
  </tr>
</tbody></table></div>

<h2 id="taimen" is-upgraded="">"taimen" for Pixel 2 XL</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="taimenopd1.170816.010">
    <td>8.0.0 (OPD1.170816.010, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opd1.170816.010-factory-c796ddb4.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPD1.170816.010]">Link</a></td>
    <td>c796ddb4c774aa7c06b03f83adef30c3bb1d5b2e431abf711117ce18e62d5491</td>
  </tr>
  <tr id="taimenopd1.170816.011">
    <td>8.0.0 (OPD1.170816.011, Sep 2017, Telstra)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opd1.170816.011-factory-1b02df7a.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPD1.170816.011]">Link</a></td>
    <td>1b02df7a423f2638323309b4412372adcb66ce3874fb036a4642af883bee3f7b</td>
  </tr>
  <tr id="taimenopd1.170816.012">
    <td>8.0.0 (OPD1.170816.012, Sep 2017, Rogers, Fido)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opd1.170816.012-factory-20574403.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPD1.170816.012]">Link</a></td>
    <td>205744037fce9f7bc278507a7d019522ea4787f9b04493b7af653f61837e0f16</td>
  </tr>
  <tr id="taimenopd3.170816.012">
    <td>8.0.0 (OPD3.170816.012, Sep 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opd3.170816.012-factory-abe3dadf.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPD3.170816.012]">Link</a></td>
    <td>abe3dadfaa649bbdff0f014e27ec4fbeb73a7ee02a24d3fb3aaa53835a73e5db</td>
  </tr>
  <tr id="taimenopd1.170816.025">
    <td>8.0.0 (OPD1.170816.025, Nov 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opd1.170816.025-factory-907c4030.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPD1.170816.025]">Link</a></td>
    <td>907c40302ff8e63cc6d633372f33f904424bd5ec4e9e0397d7aa9a8a54621cc2</td>
  </tr>
  <tr id="taimenopd3.170816.023">
    <td>8.0.0 (OPD3.170816.023, Nov 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opd3.170816.023-factory-b8ea4687.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPD3.170816.023]">Link</a></td>
    <td>b8ea46873a20f1399cd6c4c98283ea8f4cd023a77f8e30ab263253886ba1e444</td>
  </tr>
  <tr id="taimenopm1.171019.011">
    <td>8.1.0 (OPM1.171019.011, Dec 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm1.171019.011-factory-2df1c1cb.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM1.171019.011]">Link</a></td>
    <td>2df1c1cbb1761bf63cc5919ee071c998823576c7f068b91565282248e69ee4e1</td>
  </tr>
  <tr id="taimenopm2.171019.012">
    <td>8.1.0 (OPM2.171019.012, Dec 2017, Telus Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm2.171019.012-factory-0985fde2.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM2.171019.012]">Link</a></td>
    <td>0985fde27be8cf17feebafd97b41d95ac14c559bf2a3e5d4dec40db64306fccb</td>
  </tr>
  <tr id="taimenopm1.171019.013">
    <td>8.1.0 (OPM1.171019.013, Jan 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm1.171019.013-factory-6d9954c3.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM1.171019.013]">Link</a></td>
    <td>6d9954c389ec8d252f531f9f079f4b8b9ef7ca4519478f5df765e40da924f2f6</td>
  </tr>
  <tr id="taimenopm1.171019.014">
    <td>8.1.0 (OPM1.171019.014, Jan 2018, O2/UK only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm1.171019.014-factory-2e06f724.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM1.171019.014]">Link</a></td>
    <td>2e06f724b28edf57299ea157ca08a96ea73ee325f2bf5b2639d9e165c16a3f85</td>
  </tr>
  <tr id="taimenopm1.171019.018">
    <td>8.1.0 (OPM1.171019.018, Feb 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm1.171019.018-factory-e96a86ae.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM1.171019.018]">Link</a></td>
    <td>e96a86aeaae2998ff6c3fcc5ed88cc08ed88aad1c28802b0e709833cc1d6b7b4</td>
  </tr>
  <tr id="taimenopm1.171019.021">
    <td>8.1.0 (OPM1.171019.021, Mar 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm1.171019.021-factory-55f528f1.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM1.171019.021]">Link</a></td>
    <td>55f528f1b56d736ed38dca20843657f26de11fee8e92dcf781370cc8522088cc</td>
  </tr>
  <tr id="taimenopm2.171019.029">
    <td>8.1.0 (OPM2.171019.029, Apr 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm2.171019.029-factory-2937a399.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM2.171019.029]">Link</a></td>
    <td>2937a3995f35c1ed917388afe962e9c02b0c7434c853b20689303c1819bee58b</td>
  </tr>
  <tr id="taimenopm4.171019.015.a1">
    <td>8.1.0 (OPM4.171019.015.A1, Apr 2018, Telus and Koodo Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm4.171019.015.a1-factory-6793351f.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM4.171019.015.A1]">Link</a></td>
    <td>6793351f09d778c691beb878bdc286620e393714ef55ed415e7f2322afe2e6d8</td>
  </tr>
  <tr id="taimenopm2.171019.029.b1">
    <td>8.1.0 (OPM2.171019.029.B1, May 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm2.171019.029.b1-factory-8faa494b.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM2.171019.029.B1]">Link</a></td>
    <td>8faa494b5b7aaf195160551d21cab230b37f5ae1d33acf1d85fa04915ae8bc50</td>
  </tr>
  <tr id="taimenopm4.171019.016.b1">
    <td>8.1.0 (OPM4.171019.016.B1, May 2018, Fi Carriers)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm4.171019.016.b1-factory-f28b4a9b.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM4.171019.016.B1]">Link</a></td>
    <td>f28b4a9b2c25ae32c6d0506e41f89473ef43662d197c97c49b38966abdbfdb7f</td>
  </tr>
  <tr id="taimenopm2.171026.006.c1">
    <td>8.1.0 (OPM2.171026.006.C1, Jun 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm2.171026.006.c1-factory-21236059.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM2.171026.006.C1]">Link</a></td>
    <td>2123605944b0952de2c4d84bd8b3521119a99f3264f2ccbd2d1cbad519a15df5</td>
  </tr>
  <tr id="taimenopm4.171019.021.e1">
    <td>8.1.0 (OPM4.171019.021.E1, Jun 2018, T-Mobile)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm4.171019.021.e1-factory-87ca9824.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM4.171019.021.E1]">Link</a></td>
    <td>87ca98249597ddae2ff2ed0570d9a13a7bf24f25f4c1e5e7d543421b04edffb3</td>
  </tr>
  <tr id="taimenopm2.171026.006.h1">
    <td>8.1.0 (OPM2.171026.006.H1, Jul 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm2.171026.006.h1-factory-57328312.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM2.171026.006.H1]">Link</a></td>
    <td>57328312ff7ce98f4091a80a988ef21a00a2d01d7bd54494873a408f1d0bd8ff</td>
  </tr>
  <tr id="taimenopm4.171019.021.r1">
    <td>8.1.0 (OPM4.171019.021.R1, Jul 2018, T-Mobile)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-opm4.171019.021.r1-factory-dcbe1346.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [OPM4.171019.021.R1]">Link</a></td>
    <td>dcbe1346be702a246b27da547d0be56f701835087f7d6bac47356a4ea85284a2</td>
  </tr>
  <tr id="taimenppr1.180610.009">
    <td>9.0.0 (PPR1.180610.009, Aug 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-ppr1.180610.009-factory-3fb33477.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PPR1.180610.009]">Link</a></td>
    <td>3fb334772a8d8256d4aae0420f4015e01f44703002797a851c66edd4477a9028</td>
  </tr>
  <tr id="taimenppr1.180610.011">
    <td>9.0.0 (PPR1.180610.011, Aug 2018, Telstra)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-ppr1.180610.011-factory-9f0cb004.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PPR1.180610.011]">Link</a></td>
    <td>9f0cb004c3b42789c150293aa6a6eecb0f289324ce1403befde93b106da59829</td>
  </tr>
  <tr id="taimenppr2.180905.005">
    <td>9.0.0 (PPR2.180905.005, Sep 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-ppr2.180905.005-factory-c21252d4.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PPR2.180905.005]">Link</a></td>
    <td>c21252d46416ab94fa4dd22e8f3b13de7b12e817a2a9a3c23a7a2fe805415d2b</td>
  </tr>
  <tr id="taimenppr2.181005.003">
    <td>9.0.0 (PPR2.181005.003, Oct 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-ppr2.181005.003-factory-f0a1d2c1.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PPR2.181005.003]">Link</a></td>
    <td>f0a1d2c1aa9fb4c2b15e5519d3c5606e43048ff63a7d7e862ef5647a9f08d718</td>
  </tr>
  <tr id="taimenpq1a.181105.017.a1">
    <td>9.0.0 (PQ1A.181105.017.A1, Nov 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq1a.181105.017.a1-factory-e79a94ed.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ1A.181105.017.A1]">Link</a></td>
    <td>e79a94ed6954dc9243a5f601ca37da1c54d14731005f11c279d68ad3e7bbdece</td>
  </tr>
  <tr id="taimenpq1a.181205.002">
    <td>9.0.0 (PQ1A.181205.002, Dec 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq1a.181205.002-factory-4d01cf61.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ1A.181205.002]">Link</a></td>
    <td>4d01cf614a511bfdf84928eb976a04e5f203741b5ea200db3024557244a6bbbb</td>
  </tr>
  <tr id="taimenpq1a.190105.004">
    <td>9.0.0 (PQ1A.190105.004, Jan 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq1a.190105.004-factory-1fa0246a.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ1A.190105.004]">Link</a></td>
    <td>1fa0246a1e4aa38fbf4aee0a635721ea278c9edf7f554c184626eb22f376ff54</td>
  </tr>
  <tr id="taimenpq2a.190205.002">
    <td>9.0.0 (PQ2A.190205.002, Feb 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq2a.190205.002-factory-5bf777e4.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ2A.190205.002]">Link</a></td>
    <td>5bf777e465c0f3573371b04347ab0ad085f5102a7ec350c34569a1c86be2f864</td>
  </tr>
  <tr id="taimenpq2a.190305.002">
    <td>9.0.0 (PQ2A.190305.002, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq2a.190305.002-factory-8f42be1a.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ2A.190305.002]">Link</a></td>
    <td>8f42be1a67742c3ddb7a71539ad59e036d0e256e2cee6dd0d9a9a8c7c458f1ae</td>
  </tr>
  <tr id="taimenpq2a.190405.003">
    <td>9.0.0 (PQ2A.190405.003, Apr 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq2a.190405.003-factory-3d72fe71.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ2A.190405.003]">Link</a></td>
    <td>3d72fe7129d0be55f92df8cc15b8fc9bf77db5a5043f06bb0919f896126d5d1e</td>
  </tr>
  <tr id="taimenpq3a.190505.001">
    <td>9.0.0 (PQ3A.190505.001, May 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq3a.190505.001-factory-f91e5af8.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ3A.190505.001]">Link</a></td>
    <td>f91e5af8dd8675c737b78b03c60143c14e78155d1561115a9ec1a5e3a6aacc58</td>
  </tr>
  <tr id="taimenpq3a.190605.003">
    <td>9.0.0 (PQ3A.190605.003, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq3a.190605.003-factory-59303ad9.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ3A.190605.003]">Link</a></td>
    <td>59303ad91d7876a231d72a62681c3dfd58905b759c87f12e7d085c39d4fb1a0a</td>
  </tr>
  <tr id="taimenpq3a.190705.001">
    <td>9.0.0 (PQ3A.190705.001, Jul 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq3a.190705.001-factory-884e074c.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ3A.190705.001]">Link</a></td>
    <td>884e074c374080550450d6b9356e9732043d38a5e4957aedcac9c82ec6f20fb5</td>
  </tr>
  <tr id="taimenpq3a.190801.002">
    <td>9.0.0 (PQ3A.190801.002, Aug 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-pq3a.190801.002-factory-b26aa2d7.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [PQ3A.190801.002]">Link</a></td>
    <td>b26aa2d7f03fd3ebb3d5de4840efe2614043bffac46b918f24ed8791d94f90a2</td>
  </tr>
  <tr id="taimenqp1a.190711.019">
    <td>10.0.0 (QP1A.190711.019, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-qp1a.190711.019-factory-c97ea4e8.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [QP1A.190711.019]">Link</a></td>
    <td>c97ea4e821ae88d9aa99b516f6a24db5110c171864a3200e9c6ca8dbd645eca5</td>
  </tr>
  <tr id="taimenqp1a.190711.020">
    <td>10.0.0 (QP1A.190711.020, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-qp1a.190711.020-factory-6f0233dd.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [QP1A.190711.020]">Link</a></td>
    <td>6f0233dd1c8faf8dad2324245e08ed18d8757eec99d724095941ea14e3eddeb2</td>
  </tr>
  <tr id="taimenqp1a.191005.007.a1">
    <td>10.0.0 (QP1A.191005.007.A1, Oct 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/taimen-qp1a.191005.007.a1-factory-3ed47161.zip" class="gc-analytics-event" data-category="Android Images" data-label="taimen for Pixel 2 XL [QP1A.191005.007.A1]">Link</a></td>
    <td>3ed471615bd9592c26dd372e5e418e52aafbff15552dbb14f02832f64085cb06</td>
  </tr>
</tbody></table></div>

<h2 id="walleye" is-upgraded="">"walleye" for Pixel 2</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="walleyeopd1.170816.010">
    <td>8.0.0 (OPD1.170816.010, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opd1.170816.010-factory-63083164.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPD1.170816.010]">Link</a></td>
    <td>63083164c20ee40077d0a1f54b48dc6cb861fcde03f8e5f1cbbed85a36200295</td>
  </tr>
  <tr id="walleyeopd1.170816.011">
    <td>8.0.0 (OPD1.170816.011, Sep 2017, Telstra)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opd1.170816.011-factory-cd9a3474.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPD1.170816.011]">Link</a></td>
    <td>cd9a3474ca8f281316fe5d580fc2f90a51832e4e514db28bf006a1560e97b3c8</td>
  </tr>
  <tr id="walleyeopd1.170816.012">
    <td>8.0.0 (OPD1.170816.012, Sep 2017, Rogers, Fido)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opd1.170816.012-factory-a771b8c2.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPD1.170816.012]">Link</a></td>
    <td>a771b8c2760d8f3eeeeaa94737186489ae39cbcb2a912ad3d03895de29bbb4a2</td>
  </tr>
  <tr id="walleyeopd3.170816.012">
    <td>8.0.0 (OPD3.170816.012, Sep 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opd3.170816.012-factory-9626515d.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPD3.170816.012]">Link</a></td>
    <td>9626515dd78cb1ff1cdac07b72c17ade6ea932c14011bac5c1bf0ffe8b25e16d</td>
  </tr>
  <tr id="walleyeopd1.170816.018">
    <td>8.0.0 (OPD1.170816.018, Nov 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opd1.170816.018-factory-b153660d.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPD1.170816.018]">Link</a></td>
    <td>b153660d7451973f29b1b8e1eda74f977479e4c534d77488a29c272e398ae9ff</td>
  </tr>
  <tr id="walleyeopd2.170816.015">
    <td>8.0.0 (OPD2.170816.015, Nov 2017, DTAG)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opd2.170816.015-factory-5e7a47f0.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPD2.170816.015]">Link</a></td>
    <td>5e7a47f0f4c1a9234aa4d022213cf2ed2f9fd147b0d86cc2ece0ec2d25095fd8</td>
  </tr>
  <tr id="walleyeopd3.170816.016">
    <td>8.0.0 (OPD3.170816.016, Nov 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opd3.170816.016-factory-4bc6a6f9.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPD3.170816.016]">Link</a></td>
    <td>4bc6a6f9751467b65d8aab46e40bf37e81061fb436fc70642399d2de8cb8a404</td>
  </tr>
  <tr id="walleyeopd1.170816.025">
    <td>8.0.0 (OPD1.170816.025, Nov 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opd1.170816.025-factory-4752baae.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPD1.170816.025]">Link</a></td>
    <td>4752baaee571f7d645099ad8de38ce525ebbeb182660953d0da71caacfbf8c9c</td>
  </tr>
  <tr id="walleyeopd3.170816.023">
    <td>8.0.0 (OPD3.170816.023, Nov 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opd3.170816.023-factory-f269631e.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPD3.170816.023]">Link</a></td>
    <td>f269631e3ed65d3bfe21a6ea4d143b8280571687c1ccfbe79efac34715935f79</td>
  </tr>
  <tr id="walleyeopm1.171019.011">
    <td>8.1.0 (OPM1.171019.011, Dec 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm1.171019.011-factory-f74dd4fd.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM1.171019.011]">Link</a></td>
    <td>f74dd4fd9c7816a694901b01ba922c5033acb972f5fe5e51630400e4bfb07700</td>
  </tr>
  <tr id="walleyeopm2.171019.012">
    <td>8.1.0 (OPM2.171019.012, Dec 2017, Telus Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm2.171019.012-factory-9b47e323.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM2.171019.012]">Link</a></td>
    <td>9b47e323f005402ed008b8dee5bc014dd6f89876bd6c374308860a0458df5cc0</td>
  </tr>
  <tr id="walleyeopm1.171019.013">
    <td>8.1.0 (OPM1.171019.013, Jan 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm1.171019.013-factory-56e2f2dc.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM1.171019.013]">Link</a></td>
    <td>56e2f2dcd03083cacf177b2dcadef13fa5a2f69e42a075e64a4f33beb1448887</td>
  </tr>
  <tr id="walleyeopm1.171019.014">
    <td>8.1.0 (OPM1.171019.014, Jan 2018, O2/UK only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm1.171019.014-factory-123066fb.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM1.171019.014]">Link</a></td>
    <td>123066fb33acd740fd8ccb09111b1d3d2f9c0e8e3ea119a58ece102eee98e7ed</td>
  </tr>
  <tr id="walleyeopm2.171019.016">
    <td>8.1.0 (OPM2.171019.016, Jan 2018, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm2.171019.016-factory-d162f4a5.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM2.171019.016]">Link</a></td>
    <td>d162f4a51ef5f5fa4660e6319e5a1fbf3950cbb3c77243dd8ce09b6b0ce07ec0</td>
  </tr>
  <tr id="walleyeopm1.171019.019">
    <td>8.1.0 (OPM1.171019.019, Feb 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm1.171019.019-factory-b9946689.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM1.171019.019]">Link</a></td>
    <td>b994668911759ec000d671ce73728dc23e91bef8ea4bd6947a9c274645aeb803</td>
  </tr>
  <tr id="walleyeopm1.171019.021">
    <td>8.1.0 (OPM1.171019.021, Mar 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm1.171019.021-factory-ab7d4133.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM1.171019.021]">Link</a></td>
    <td>ab7d4133548a10d6983e377e2c65d4287d37bf28901569f2039464dde63909f1</td>
  </tr>
  <tr id="walleyeopm2.171019.029">
    <td>8.1.0 (OPM2.171019.029, Apr 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm2.171019.029-factory-41296266.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM2.171019.029]">Link</a></td>
    <td>4129626633cbab200c6c18fc52b2dd832714ef96761e1866b60d462e4dd39cac</td>
  </tr>
  <tr id="walleyeopm4.171019.015.a1">
    <td>8.1.0 (OPM4.171019.015.A1, Apr 2018, Telus and Koodo Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm4.171019.015.a1-factory-a9124507.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM4.171019.015.A1]">Link</a></td>
    <td>a91245077caf240831a835b26d0b44d703d702fbec29ec320abb31aa10f68ebb</td>
  </tr>
  <tr id="walleyeopm2.171019.029.b1">
    <td>8.1.0 (OPM2.171019.029.B1, May 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm2.171019.029.b1-factory-f3086353.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM2.171019.029.B1]">Link</a></td>
    <td>f30863534452ad2a899d874c0bc31c95ff1595d1b3c558f9d5c805120a851bde</td>
  </tr>
  <tr id="walleyeopm4.171019.016.b1">
    <td>8.1.0 (OPM4.171019.016.B1, May 2018, Fi Carriers)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm4.171019.016.b1-factory-6f46fa22.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM4.171019.016.B1]">Link</a></td>
    <td>6f46fa2228cc1aff8a990851c13c46c0dd6e372139b35a605814bb21ef0430b9</td>
  </tr>
  <tr id="walleyeopm2.171026.006.c1">
    <td>8.1.0 (OPM2.171026.006.C1, Jun 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm2.171026.006.c1-factory-1c0e0e5a.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM2.171026.006.C1]">Link</a></td>
    <td>1c0e0e5aa24feab53fbb43d26d246c485f166bc7eb67e1e07345b502ffa51c60</td>
  </tr>
  <tr id="walleyeopm4.171019.021.e1">
    <td>8.1.0 (OPM4.171019.021.E1, Jun 2018, T-Mobile)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm4.171019.021.e1-factory-5a35d247.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM4.171019.021.E1]">Link</a></td>
    <td>5a35d247ab5cdd5150b9d7417667123757d2e16b5ca40ac4c9a8a4de4c3d329c</td>
  </tr>
  <tr id="walleyeopm2.171026.006.g1">
    <td>8.1.0 (OPM2.171026.006.G1, Jul 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm2.171026.006.g1-factory-f7f5a622.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM2.171026.006.G1]">Link</a></td>
    <td>f7f5a6228b5e5a7b3e9de82fcbb98b313c448dfdd5c43d58525d4b9ed49b3eef</td>
  </tr>
  <tr id="walleyeopm4.171019.021.q1">
    <td>8.1.0 (OPM4.171019.021.Q1, Jul 2018, T-Mobile)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-opm4.171019.021.q1-factory-a4b25146.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [OPM4.171019.021.Q1]">Link</a></td>
    <td>a4b251468a0a6236088f78cba6ddca7038fbb90acb4e0a4e331f0295177fba0c</td>
  </tr>
  <tr id="walleyeppr1.180610.009">
    <td>9.0.0 (PPR1.180610.009, Aug 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-ppr1.180610.009-factory-4149f7e5.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PPR1.180610.009]">Link</a></td>
    <td>4149f7e5a7ea4b852910d6d25f2d594d07f20e9781cf8e6e9585f0a33edb54ce</td>
  </tr>
  <tr id="walleyeppr1.180610.011">
    <td>9.0.0 (PPR1.180610.011, Aug 2018, Telstra)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-ppr1.180610.011-factory-0fbd3048.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PPR1.180610.011]">Link</a></td>
    <td>0fbd304845b6a1e8c5960deedb70aab0f804a4b1bb93242b3bbcdad586982769</td>
  </tr>
  <tr id="walleyeppr2.180905.005">
    <td>9.0.0 (PPR2.180905.005, Sep 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-ppr2.180905.005-factory-4895938f.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PPR2.180905.005]">Link</a></td>
    <td>4895938f17a317c1373c37480c33b09f7d2d531cd3d4275d2c2773c103c9370a</td>
  </tr>
  <tr id="walleyeppr2.181005.003">
    <td>9.0.0 (PPR2.181005.003, Oct 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-ppr2.181005.003-factory-8613da61.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PPR2.181005.003]">Link</a></td>
    <td>8613da61efa69e8aaac416b7c26e239843a2829876a61c462707530a87a8dffb</td>
  </tr>
  <tr id="walleyepq1a.181105.017.a1">
    <td>9.0.0 (PQ1A.181105.017.A1, Nov 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq1a.181105.017.a1-factory-408e5a32.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ1A.181105.017.A1]">Link</a></td>
    <td>408e5a32abf252fb4acdf72c0ba98a39397807ae87031104825ea9cadb09a515</td>
  </tr>
  <tr id="walleyepq1a.181205.002">
    <td>9.0.0 (PQ1A.181205.002, Dec 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq1a.181205.002-factory-fb27eb5a.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ1A.181205.002]">Link</a></td>
    <td>fb27eb5ac91d339f5cc426fdd8202db7579d0ee72b7b2674d67d4449c342066d</td>
  </tr>
  <tr id="walleyepq1a.190105.004">
    <td>9.0.0 (PQ1A.190105.004, Jan 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq1a.190105.004-factory-78374c71.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ1A.190105.004]">Link</a></td>
    <td>78374c71a13d5edc72424b46e08f05dc9fa9e5e53af452fd3be48d8c3346bb41</td>
  </tr>
  <tr id="walleyepq2a.190205.002">
    <td>9.0.0 (PQ2A.190205.002, Feb 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq2a.190205.002-factory-781881b5.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ2A.190205.002]">Link</a></td>
    <td>781881b5f420246a5da8c1ff72977d58867b0743805ea2e410cc46d9356a02cf</td>
  </tr>
  <tr id="walleyepq2a.190305.002">
    <td>9.0.0 (PQ2A.190305.002, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq2a.190305.002-factory-73bd98de.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ2A.190305.002]">Link</a></td>
    <td>73bd98dee9844d0322e84a134ba541fa682061446cfe32cd8d88ae803d971a30</td>
  </tr>
  <tr id="walleyepq2a.190405.003">
    <td>9.0.0 (PQ2A.190405.003, Apr 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq2a.190405.003-factory-e9a0ea4c.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ2A.190405.003]">Link</a></td>
    <td>e9a0ea4ca785784e23004033e13b6ba3610e31257c21609689c089190bb254c6</td>
  </tr>
  <tr id="walleyepq3a.190505.001">
    <td>9.0.0 (PQ3A.190505.001, May 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq3a.190505.001-factory-d2730d9c.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ3A.190505.001]">Link</a></td>
    <td>d2730d9cd155ada199c7c9d90eebb4e43cc7e2702f6853e59e2f79d4be6be291</td>
  </tr>
  <tr id="walleyepq3a.190605.003">
    <td>9.0.0 (PQ3A.190605.003, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq3a.190605.003-factory-952d65cf.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ3A.190605.003]">Link</a></td>
    <td>952d65cf3904e2d88a1f80a935c5b5f017494f8758e8d8706c29e3b1f5bd1eaa</td>
  </tr>
  <tr id="walleyepq3a.190705.001">
    <td>9.0.0 (PQ3A.190705.001, Jul 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq3a.190705.001-factory-cc471c8c.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ3A.190705.001]">Link</a></td>
    <td>cc471c8c7ffaa899e30438fa30b8d33b92b12a3c92d3e592c53bfc5983de205b</td>
  </tr>
  <tr id="walleyepq3a.190801.002">
    <td>9.0.0 (PQ3A.190801.002, Aug 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-pq3a.190801.002-factory-f9a5e230.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [PQ3A.190801.002]">Link</a></td>
    <td>f9a5e2307ff6d36afc94899f88d094e4468e9211e5181cfc5d0db5ff4ab417f2</td>
  </tr>
  <tr id="walleyeqp1a.190711.019">
    <td>10.0.0 (QP1A.190711.019, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-qp1a.190711.019-factory-c6730808.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [QP1A.190711.019]">Link</a></td>
    <td>c6730808415aaf2246fb7ba2e2da2d538368d92c6f1e743ad5df36b812792e40</td>
  </tr>
  <tr id="walleyeqp1a.190711.020">
    <td>10.0.0 (QP1A.190711.020, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-qp1a.190711.020-factory-fa9552ea.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [QP1A.190711.020]">Link</a></td>
    <td>fa9552eaef3531e2abae09b5e3aae510b7a052f6938a145dc1caed8b98a146c4</td>
  </tr>
  <tr id="walleyeqp1a.191005.007.a1">
    <td>10.0.0 (QP1A.191005.007.A1, Oct 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/walleye-qp1a.191005.007.a1-factory-78ad96e7.zip" class="gc-analytics-event" data-category="Android Images" data-label="walleye for Pixel 2 [QP1A.191005.007.A1]">Link</a></td>
    <td>78ad96e7de96b9fd24033b978e9bd4c7546ca9c46e0ef818b174d46bc9234b13</td>
  </tr>
</tbody></table></div>

<h2 id="marlin" is-upgraded="">"marlin" for Pixel XL</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="marlinnde63h">
    <td>7.1.0 (NDE63H, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nde63h-factory-96adcecf.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NDE63H]">Link</a></td>
    <td>96adcecf136d0389569e28a3396eba92880d77df3ceb8e39b0a765d99ddf0929</td>
  </tr>
  <tr id="marlinnde63l">
    <td>7.1.0 (NDE63L, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nde63l-factory-71a65e7e.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NDE63L]">Link</a></td>
    <td>71a65e7ef49f88a8f376831378984c019e8f078dbd39499eb4ca9e1a475df9f0</td>
  </tr>
  <tr id="marlinnde63p">
    <td>7.1.0 (NDE63P, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nde63p-factory-dcdaaa51.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NDE63P]">Link</a></td>
    <td>dcdaaa51d4b4c0a67c4b670f76fe53b852b38d7b2ce65399ac56799bfc1ca7bb</td>
  </tr>
  <tr id="marlinnde63u">
    <td>7.1.0 (Europe, NDE63U, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nde63u-factory-24e8abeb.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NDE63U]">Link</a></td>
    <td>24e8abeb4e1f09bff31577b46661110bf7d5745abb9269b638f6fb86a338d271</td>
  </tr>
  <tr id="marlinnde63v">
    <td>7.1.0 (NDE63V, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nde63v-factory-a66866ba.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NDE63V]">Link</a></td>
    <td>a66866ba4b8f9f1baa856828d46a747d769098add86098bece50854983ecea3e</td>
  </tr>
  <tr id="marlinnde63x">
    <td>7.1.0 (Verizon, NDE63X, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nde63x-factory-8b520419.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NDE63X]">Link</a></td>
    <td>8b520419e32141f68d9f12d7e302bfb77885ed5587908d30b2a0e94ed07038a7</td>
  </tr>
  <tr id="marlinnmf26o">
    <td>7.1.1 (NMF26O, Dec 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nmf26o-factory-4f68765c.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NMF26O]">Link</a></td>
    <td>4f68765c108fc3d45ece7bca8e873561e29c5ee83c8671f1b7785f57a8888070</td>
  </tr>
  <tr id="marlinnmf26q">
    <td>7.1.1 (NMF26Q, Dec 2016, Europe/O2)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nmf26q-factory-5d515cbc.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NMF26Q]">Link</a></td>
    <td>5d515cbc8d5b98bc36375355ef34af73e27afdfd0a1f7f0bde6ca8fe4cca6564</td>
  </tr>
  <tr id="marlinnmf26u">
    <td>7.1.1 (NMF26U, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nmf26u-factory-10ffd61d.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NMF26U]">Link</a></td>
    <td>10ffd61d7cf7c62a77ad04cc6dc2a4ba2fc9f7655b63bcb87ffdee7558c33661</td>
  </tr>
  <tr id="marlinnmf26v">
    <td>7.1.1 (NMF26V, Jan 2017, Europe/O2)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nmf26v-factory-e6bda208.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NMF26V]">Link</a></td>
    <td>e6bda2087d010f86589e799dae19d56d7beff307251bd2820693cfac360e65e8</td>
  </tr>
  <tr id="marlinnof26v">
    <td>7.1.1 (NOF26V, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nof26v-factory-1dce14a1.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NOF26V]">Link</a></td>
    <td>1dce14a1cde69ac72e14894c980a823920885c78410d8f1b431565517a56e72f</td>
  </tr>
  <tr id="marlinnof26w">
    <td>7.1.1 (NOF26W, Feb 2017, Rogers Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nof26w-factory-d2cb0574.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NOF26W]">Link</a></td>
    <td>d2cb05747fbd11e2590faf3c4675bd32e61e5aa401d7548786ef0fed17096968</td>
  </tr>
  <tr id="marlinnof27b">
    <td>7.1.1 (NOF27B, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nof27b-factory-2259c206.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NOF27B]">Link</a></td>
    <td>2259c206286971ef7a48cee8bdad9f5fb9914e9dccb282d96ba0b6385eb20072</td>
  </tr>
  <tr id="marlinnof27c">
    <td>7.1.1 (NOF27C, Mar 2017, Rogers Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nof27c-factory-b49c0e7b.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NOF27C]">Link</a></td>
    <td>b49c0e7b058564efb6deb9278dac9263124b2341bf9660accdc56fbceb90e623</td>
  </tr>
  <tr id="marlinnof27d">
    <td>7.1.1 (NOF27D, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nof27d-factory-01a800f0.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NOF27D]">Link</a></td>
    <td>01a800f05ac28216632b4a38976517c7812bd8381cd411d04151f61ab2dbc041</td>
  </tr>
  <tr id="marlinn2g47e">
    <td>7.1.2 (N2G47E, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-n2g47e-factory-ebc79a0b.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [N2G47E]">Link</a></td>
    <td>ebc79a0b5015bd1d5d8d72c3a984cbf0de6e8d5bd26ab93fd2afcc9791199fc1</td>
  </tr>
  <tr id="marlinn2g47j">
    <td>7.1.2 (N2G47J, Apr 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-n2g47j-factory-503d88f5.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [N2G47J]">Link</a></td>
    <td>503d88f556a481677ecaadb62e83fa3a2b73f103271b954f629838f45ea4168a</td>
  </tr>
  <tr id="marlinnhg47k">
    <td>7.1.2 (NHG47K, Apr 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nhg47k-factory-fc027c3b.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NHG47K]">Link</a></td>
    <td>fc027c3b428914d1a52fae80d88f5d3fd4f7ce9ac055edaa571ae5afcb85044d</td>
  </tr>
  <tr id="marlinn2g47o">
    <td>7.1.2 (N2G47O, May 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-n2g47o-factory-7150cd63.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [N2G47O]">Link</a></td>
    <td>7150cd63ebb56bdb518a9915116773f6541cea7f01540580151d2ceb0814b65d</td>
  </tr>
  <tr id="marlinn2g47t">
    <td>7.1.2 (N2G47T, May 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-n2g47t-factory-a25a7b1b.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [N2G47T]">Link</a></td>
    <td>a25a7b1b3d0cc3bbacde793348ea7c35d5e89b7d6ae7c0dd2831a7715580e870</td>
  </tr>
  <tr id="marlinnhg47l">
    <td>7.1.2 (NHG47L, May 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nhg47l-factory-df005737.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NHG47L]">Link</a></td>
    <td>df0057379caccbab2184c79258686de5fa1c7946d42326c912b5b607a22fa654</td>
  </tr>
  <tr id="marlinnhg47n">
    <td>7.1.2 (NHG47N, Jun 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nhg47n-factory-61938704.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NHG47N]">Link</a></td>
    <td>61938704ed1a67daa281ef6516fa59316829e51e431413a512bea3b673c47721</td>
  </tr>
  <tr id="marlinnjh34c">
    <td>7.1.2 (NJH34C, Jun 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-njh34c-factory-be914eaa.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NJH34C]">Link</a></td>
    <td>be914eaa15adb62dfec8bbd8856ce538f738f25d59a8c861ede6b053d0b773c2</td>
  </tr>
  <tr id="marlinnjh47b">
    <td>7.1.2 (NJH47B, Jun 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-njh47b-factory-12f9e64e.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NJH47B]">Link</a></td>
    <td>12f9e64e0aa9488a200023dc2544af3d878a5d1a09836d6473a4ced4bf954e3f</td>
  </tr>
  <tr id="marlinnkg47l">
    <td>7.1.2 (NKG47L, Jun 2017, T-Mobile, Fi carriers, and Rogers)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nkg47l-factory-9fbf9d8e.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NKG47L]">Link</a></td>
    <td>9fbf9d8ef0e5977799e1d7637b65914f0f5fcfaaf774fd1758739d8e6ce4f0ca</td>
  </tr>
  <tr id="marlinnhg47o">
    <td>7.1.2 (NHG47O, Jul 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nhg47o-factory-a2b41619.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NHG47O]">Link</a></td>
    <td>a2b41619842a7fc8b7bb5fc13e052337b3fffca68cf26b12d5292188fe25db52</td>
  </tr>
  <tr id="marlinnjh47d">
    <td>7.1.2 (NJH47D, Jul 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-njh47d-factory-5ba1ef91.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NJH47D]">Link</a></td>
    <td>5ba1ef91e32a9fe527240050092ec4b8c781c7979a6d043d0363d187360ef31c</td>
  </tr>
  <tr id="marlinnkg47m">
    <td>7.1.2 (NKG47M, Jul 2017, T-Mobile, Fi carriers)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nkg47m-factory-f0fa887a.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NKG47M]">Link</a></td>
    <td>f0fa887a31e39b00db5d957ea2d575205fd7627cacdb2c7c79fb6cdfe1e9f182</td>
  </tr>
  <tr id="marlinnzh54b">
    <td>7.1.2 (NZH54B, Jul 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nzh54b-factory-857c0179.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NZH54B]">Link</a></td>
    <td>857c01792c36278c8758b3e14a1ee0c5b4123e6afab1fffc380b80c232058b30</td>
  </tr>
  <tr id="marlinnhg47q">
    <td>7.1.2 (NHG47Q, Aug 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nhg47q-factory-8b788af8.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NHG47Q]">Link</a></td>
    <td>8b788af852d231a6ad99324aaed38f093ca07d4ad771b80609be7bf0d7033c2c</td>
  </tr>
  <tr id="marlinnjh47f">
    <td>7.1.2 (NJH47F, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-njh47f-factory-497f7f66.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NJH47F]">Link</a></td>
    <td>497f7f663a8f31418ff4de343d123e70946e03253bceb908b1ac3ab87c72093f</td>
  </tr>
  <tr id="marlinnkg47s">
    <td>7.1.2 (NKG47S, Aug 2017, T-Mobile, Fi carriers, and Rogers)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nkg47s-factory-a434e157.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NKG47S]">Link</a></td>
    <td>a434e157f855427c929113e16aa5f54b73c135ea0fc5ae5fbac9ee8a08393ad8</td>
  </tr>
  <tr id="marlinnzh54d">
    <td>7.1.2 (NZH54D, Aug 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-nzh54d-factory-d34033fa.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [NZH54D]">Link</a></td>
    <td>d34033faf5631fb66f8bc31d26928bb69a97c71b621e93ccd4edca0bf259313a</td>
  </tr>
  <tr id="marlinopr6.170623.011">
    <td>8.0.0 (OPR6.170623.011, Aug 2017, Bell, Telus, Telstra, TMO, Sprint, USCC, Rogers/Fido)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opr6.170623.011-factory-985fd412.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPR6.170623.011]">Link</a></td>
    <td>985fd412c40dd1ec6ee780185b30c5854627b5301da2a48f252155a0265116de</td>
  </tr>
  <tr id="marlinopr6.170623.012">
    <td>8.0.0 (OPR6.170623.012, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opr6.170623.012-factory-6304451d.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPR6.170623.012]">Link</a></td>
    <td>6304451dd6744b1a2faadd7921f28a217e8dbe4bf20c6cfc20bf350b1e0f07df</td>
  </tr>
  <tr id="marlinopr1.170623.026">
    <td>8.0.0 (OPR1.170623.026, Sep 2017, Fi/Canada)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opr1.170623.026-factory-1ed9b4b2.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPR1.170623.026]">Link</a></td>
    <td>1ed9b4b2cf045e04b8506eaa4927d7825d65d02460f5755d08549150dc411985</td>
  </tr>
  <tr id="marlinopr3.170623.007">
    <td>8.0.0 (OPR3.170623.007, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opr3.170623.007-factory-bf187b02.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPR3.170623.007]">Link</a></td>
    <td>bf187b023f59fe92dfd7d2b9492ad9f319ee4e10b8435d421204cc5dbbe47110</td>
  </tr>
  <tr id="marlinopr1.170623.027">
    <td>8.0.0 (OPR1.170623.027, Oct 2017, Fi/Canada)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opr1.170623.027-factory-c3d7fe5d.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPR1.170623.027]">Link</a></td>
    <td>c3d7fe5d445492d72ecedb11ce332af4f198c0bfc2933ed62161673a90261582</td>
  </tr>
  <tr id="marlinopr3.170623.008">
    <td>8.0.0 (OPR3.170623.008, Oct 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opr3.170623.008-factory-2079f009.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPR3.170623.008]">Link</a></td>
    <td>2079f0098bf999fae5d25956c96da17698649c8bf5fa8e2d9bfb95ff5d33a563</td>
  </tr>
  <tr id="marlinopr1.170623.032">
    <td>8.0.0 (OPR1.170623.032, Nov 2017, Fi/Canada)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opr1.170623.032-factory-990d8d51.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPR1.170623.032]">Link</a></td>
    <td>990d8d518fe2a2bcab17e01410866b3bf6cb75ff4aa7b2d1a345b79042f00573</td>
  </tr>
  <tr id="marlinopr3.170623.013">
    <td>8.0.0 (OPR3.170623.013, Nov 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opr3.170623.013-factory-af0b6564.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPR3.170623.013]">Link</a></td>
    <td>af0b65646b391da6f8386421fbc65fe4de859d9f6db526ae7fef79f0712d3d90</td>
  </tr>
  <tr id="marlinopm1.171019.011">
    <td>8.1.0 (OPM1.171019.011, Dec 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opm1.171019.011-factory-fe9d06f3.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPM1.171019.011]">Link</a></td>
    <td>fe9d06f36e908d7267614697bc83a3fa04fcbe83667c12bff977b8ac6a7ca856</td>
  </tr>
  <tr id="marlinopm1.171019.012">
    <td>8.1.0 (OPM1.171019.012, Jan 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opm1.171019.012-factory-b7b24003.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPM1.171019.012]">Link</a></td>
    <td>b7b24003e805360c09c9798770d0c4280d977264e93815e7a8394560598c65bb</td>
  </tr>
  <tr id="marlinopm1.171019.014">
    <td>8.1.0 (OPM1.171019.014, Jan 2018, O2/UK only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opm1.171019.014-factory-3ab03172.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPM1.171019.014]">Link</a></td>
    <td>3ab03172cdc0e1bdd56af3f59a978b35c3b0935cf6c546f9e144608f716d679d</td>
  </tr>
  <tr id="marlinopm1.171019.016">
    <td>8.1.0 (OPM1.171019.016, Feb 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opm1.171019.016-factory-5d034d9a.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPM1.171019.016]">Link</a></td>
    <td>5d034d9ab6aeb0880c9d60b0cb743830629f24d2ffa154b93a0e2806958b50b0</td>
  </tr>
  <tr id="marlinopm1.171019.021">
    <td>8.1.0 (OPM1.171019.021, Mar 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opm1.171019.021-factory-eb9f8156.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPM1.171019.021]">Link</a></td>
    <td>eb9f8156dcc88fee3800cd9b9bbac62b2bf23a5f175cb2b9e0f90d53d5cbd465</td>
  </tr>
  <tr id="marlinopm2.171019.029">
    <td>8.1.0 (OPM2.171019.029, Apr 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opm2.171019.029-factory-96b864b3.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPM2.171019.029]">Link</a></td>
    <td>96b864b33a719d382d8d50c2113bb9333cf67f2fa5147c9616e882e4787ebfca</td>
  </tr>
  <tr id="marlinopm4.171019.016.b1">
    <td>8.1.0 (OPM4.171019.016.B1, May 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opm4.171019.016.b1-factory-77cb10f1.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPM4.171019.016.B1]">Link</a></td>
    <td>77cb10f105425713b23d3f9b488a9da54b861ed282548968bb868f539f4b47c4</td>
  </tr>
  <tr id="marlinopm4.171019.021.d1">
    <td>8.1.0 (OPM4.171019.021.D1, Jun 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opm4.171019.021.d1-factory-19d49a07.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPM4.171019.021.D1]">Link</a></td>
    <td>19d49a07453c6f7cdcf539bc67291cf389b9099fe01153f18a68b91a0db938ae</td>
  </tr>
  <tr id="marlinopm4.171019.021.p1">
    <td>8.1.0 (OPM4.171019.021.P1, Jul 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-opm4.171019.021.p1-factory-d5fc023e.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [OPM4.171019.021.P1]">Link</a></td>
    <td>d5fc023e90f37c8d353f331411a22131aa41cf6f0047401bf03747039b8fa2a7</td>
  </tr>
  <tr id="marlinppr1.180610.009">
    <td>9.0.0 (PPR1.180610.009, Aug 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-ppr1.180610.009-factory-90a4fa8b.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PPR1.180610.009]">Link</a></td>
    <td>90a4fa8b99796aad1a2347dd4399aa89db9bc7da3e573749136ab0713246e97d</td>
  </tr>
  <tr id="marlinppr1.180610.010">
    <td>9.0.0 (PPR1.180610.010, Aug 2018, Telus)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-ppr1.180610.010-factory-3b90270c.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PPR1.180610.010]">Link</a></td>
    <td>3b90270cd90527298e2679ba5dafe89508949254e10a6865a5ecf4b4a6975b08</td>
  </tr>
  <tr id="marlinppr1.180905.003">
    <td>9.0.0 (PPR1.180905.003, Sep 2018, Telus)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-ppr1.180905.003-factory-051c4ec5.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PPR1.180905.003]">Link</a></td>
    <td>051c4ec5c33c6a948a48c9c83b36c73c976b320d3ddbc0bf15f9468d61c76a0c</td>
  </tr>
  <tr id="marlinppr2.180905.006">
    <td>9.0.0 (PPR2.180905.006, Sep 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-ppr2.180905.006-factory-df8ec974.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PPR2.180905.006]">Link</a></td>
    <td>df8ec9745c436000568af9b4205f5ba3c1fe67e164cad4f906a77458c3a656fb</td>
  </tr>
  <tr id="marlinppr2.180905.006.a1">
    <td>9.0.0 (PPR2.180905.006.A1, Sep 2018, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-ppr2.180905.006.a1-factory-a78fe264.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PPR2.180905.006.A1]">Link</a></td>
    <td>a78fe26434e04f8d5015bab79f717fc7b03b13286370b079b7e96d1f7562512a</td>
  </tr>
  <tr id="marlinppr1.181005.003">
    <td>9.0.0 (PPR1.181005.003, Oct 2018, Telus Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-ppr1.181005.003-factory-87fbdecc.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PPR1.181005.003]">Link</a></td>
    <td>87fbdecc08c8e9cabd17449118d9cc3df4db3e82663280200867dc04b25d7ee8</td>
  </tr>
  <tr id="marlinppr2.181005.003">
    <td>9.0.0 (PPR2.181005.003, Oct 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-ppr2.181005.003-factory-59b2d3dd.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PPR2.181005.003]">Link</a></td>
    <td>59b2d3ddc0ee8b42f88cceb01f2a52cbca5028af1969e7abaade3424688b935d</td>
  </tr>
  <tr id="marlinppr1.181005.003.a1">
    <td>9.0.0 (PPR1.181005.003.A1, Nov 2018, Telus Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-ppr1.181005.003.a1-factory-960a173f.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PPR1.181005.003.A1]">Link</a></td>
    <td>960a173f0f84e2c3c0c5d96643e6ca3f99d5a898a932c6e3a62c52282d6fb3f4</td>
  </tr>
  <tr id="marlinppr2.181005.003.a1">
    <td>9.0.0 (PPR2.181005.003.A1, Nov 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-ppr2.181005.003.a1-factory-918e249f.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PPR2.181005.003.A1]">Link</a></td>
    <td>918e249f00d79941799d0e8f09f539ad8e52d8188eaaef6c10a4360880093dee</td>
  </tr>
  <tr id="marlinpq1a.181205.002.a1">
    <td>9.0.0 (PQ1A.181205.002.A1, Dec 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-pq1a.181205.002.a1-factory-9a129f3e.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PQ1A.181205.002.A1]">Link</a></td>
    <td>9a129f3e1bed577fd87078042384648ce88d541d0d76ced3bc08bd78626adadd</td>
  </tr>
  <tr id="marlinpq1a.190105.004">
    <td>9.0.0 (PQ1A.190105.004, Jan 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-pq1a.190105.004-factory-2a6c1b27.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PQ1A.190105.004]">Link</a></td>
    <td>2a6c1b278b0a07561a1080f4c0017fb9628654d12f55c20775501477ce5af700</td>
  </tr>
  <tr id="marlinpq2a.190205.003">
    <td>9.0.0 (PQ2A.190205.003, Feb 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-pq2a.190205.003-factory-8a9a1ff8.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PQ2A.190205.003]">Link</a></td>
    <td>8a9a1ff816b8d117c60c44db8e4b9dd84bc07ea9b95c3745d17e6cad349b4b38</td>
  </tr>
  <tr id="marlinpq2a.190305.002">
    <td>9.0.0 (PQ2A.190305.002, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-pq2a.190305.002-factory-adea2e11.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PQ2A.190305.002]">Link</a></td>
    <td>adea2e1109a841867f336f91087274e90cdec36a7c9a5f8a78f5bcf500f570d8</td>
  </tr>
  <tr id="marlinpq2a.190405.003">
    <td>9.0.0 (PQ2A.190405.003, Apr 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-pq2a.190405.003-factory-d30b60f0.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PQ2A.190405.003]">Link</a></td>
    <td>d30b60f0716850430dad505b928b917d61c502603250b4e7e9206a086f62b106</td>
  </tr>
  <tr id="marlinpq3a.190505.001">
    <td>9.0.0 (PQ3A.190505.001, May 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-pq3a.190505.001-factory-5dac573c.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PQ3A.190505.001]">Link</a></td>
    <td>5dac573cedb98a1c8b8e9cf0bf87710e9f0d32a4290ed2339412fdc437fca331</td>
  </tr>
  <tr id="marlinpq3a.190605.003">
    <td>9.0.0 (PQ3A.190605.003, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-pq3a.190605.003-factory-14ebecf7.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PQ3A.190605.003]">Link</a></td>
    <td>14ebecf79fdfdbe2eba81470180942cd643be21c9ecf2cc86bc3e89d0e9dd0bf</td>
  </tr>
  <tr id="marlinpq3a.190705.001">
    <td>9.0.0 (PQ3A.190705.001, Jul 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-pq3a.190705.001-factory-522f27c4.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PQ3A.190705.001]">Link</a></td>
    <td>522f27c4d50055f6402ca9d4d62fb07425e3af7c4766b647a4096ce3041984ba</td>
  </tr>
  <tr id="marlinpq3a.190801.002">
    <td>9.0.0 (PQ3A.190801.002, Aug 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-pq3a.190801.002-factory-13dbb265.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [PQ3A.190801.002]">Link</a></td>
    <td>13dbb265fb7ab74473905705d2e34d019ffc0bae601d1193e71661133aba9653</td>
  </tr>
  <tr id="marlinqp1a.190711.019">
    <td>10.0.0 (QP1A.190711.019, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-qp1a.190711.019-factory-3f4a20df.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [QP1A.190711.019]">Link</a></td>
    <td>3f4a20df5868981e6af189c88fd09e17ba042b5955dffac8593b48b14d6ae85c</td>
  </tr>
  <tr id="marlinqp1a.190711.020">
    <td>10.0.0 (QP1A.190711.020, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-qp1a.190711.020-factory-2db5273a.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [QP1A.190711.020]">Link</a></td>
    <td>2db5273a273a491fee3e175f3018830fc58015bdbacfedb589d67acf123156f8</td>
  </tr>
  <tr id="marlinqp1a.191005.007.a1">
    <td>10.0.0 (QP1A.191005.007.A1, Oct 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/marlin-qp1a.191005.007.a1-factory-c27241e0.zip" class="gc-analytics-event" data-category="Android Images" data-label="marlin for Pixel XL [QP1A.191005.007.A1]">Link</a></td>
    <td>c27241e0aaf46f4ff60d8279efd9ac6f6ac8e80b1bd08c43d75f851313efaa12</td>
  </tr>
</tbody></table></div>

<h2 id="sailfish" is-upgraded="">"sailfish" for Pixel</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="sailfishnde63h">
    <td>7.1.0 (NDE63H, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nde63h-factory-43ba5f81.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NDE63H]">Link</a></td>
    <td>43ba5f8130a58770edce6cb0c6c43920798e038cd7cdec2c54f22a1dd474a7c8</td>
  </tr>
  <tr id="sailfishnde63l">
    <td>7.1.0 (NDE63L, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nde63l-factory-49876a7c.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NDE63L]">Link</a></td>
    <td>49876a7c9e8f14da672dad27a0e404cccbb1330a4c9ebd398c34583a576eba6c</td>
  </tr>
  <tr id="sailfishnde63p">
    <td>7.1.0 (NDE63P, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nde63p-factory-aaaa2f1a.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NDE63P]">Link</a></td>
    <td>aaaa2f1a592ba43de10396938220c4ed65ff3341edd01afd4b5a4f506b39042c</td>
  </tr>
  <tr id="sailfishnde63u">
    <td>7.1.0 (Europe, NDE63U, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nde63u-factory-3fa36709.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NDE63U]">Link</a></td>
    <td>3fa367096c251cd5ab1a6c465cb60fc075b08b999148bbf0036f1533e3efd364</td>
  </tr>
  <tr id="sailfishnde63v">
    <td>7.1.0 (NDE63V, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nde63v-factory-1b3155ff.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NDE63V]">Link</a></td>
    <td>1b3155ff623e8a872a788c54e650a0077175f54d723a185f52fff8a3170478ff</td>
  </tr>
  <tr id="sailfishnde63x">
    <td>7.1.0 (Verizon, NDE63X, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nde63x-factory-dc45f6c8.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NDE63X]">Link</a></td>
    <td>dc45f6c83547266bf9e49edeae0978c3d734278febec2f7023aae4bf299e4fec</td>
  </tr>
  <tr id="sailfishnmf26o">
    <td>7.1.1 (NMF26O, Dec 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nmf26o-factory-58719f26.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NMF26O]">Link</a></td>
    <td>58719f26685322bc1c7bc0a313746ceaec6772499913fc671d58f4f0150a9278</td>
  </tr>
  <tr id="sailfishnmf26q">
    <td>7.1.1 (NMF26Q, Dec 2016, Europe/O2)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nmf26q-factory-a84e0e4b.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NMF26Q]">Link</a></td>
    <td>a84e0e4b2f80bf8b88857cbde28e0617380a94590dcfc24713aa1bc1ec3671fb</td>
  </tr>
  <tr id="sailfishnmf26u">
    <td>7.1.1 (NMF26U, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nmf26u-factory-b161fe98.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NMF26U]">Link</a></td>
    <td>b161fe98c4308b7e611ca3e432a8ba7141c2cb607b63e2b7e3e7a39c7d1c4943</td>
  </tr>
  <tr id="sailfishnmf26v">
    <td>7.1.1 (NMF26V, Jan 2017, Europe/O2)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nmf26v-factory-8ba1f89e.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NMF26V]">Link</a></td>
    <td>8ba1f89e1db6cf9a770abc065a63db96ac9ac00613a7ec088ccb35440feb645e</td>
  </tr>
  <tr id="sailfishnof26v">
    <td>7.1.1 (NOF26V, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nof26v-factory-65092b38.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NOF26V]">Link</a></td>
    <td>65092b3813a769483af3b810635452c8e016b19f71c1920a8c33711ab875b84f</td>
  </tr>
  <tr id="sailfishnof26w">
    <td>7.1.1 (NOF26W, Feb 2017, Rogers Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nof26w-factory-277fc900.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NOF26W]">Link</a></td>
    <td>277fc9006dca8b34bfc616b4bf83626d84271f7555e2c1aa41248cd68d481e13</td>
  </tr>
  <tr id="sailfishnof27b">
    <td>7.1.1 (NOF27B, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nof27b-factory-5a8a6e11.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NOF27B]">Link</a></td>
    <td>5a8a6e118af74588e9be13a5a6bd0d620b95067a6f7c5f808ae1c04739398400</td>
  </tr>
  <tr id="sailfishnof27c">
    <td>7.1.1 (NOF27C, Mar 2017, Rogers Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nof27c-factory-2451ef01.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NOF27C]">Link</a></td>
    <td>2451ef017181043e83820f7340c8ef479bca5b927f56b16b9a3c3ca598dd1460</td>
  </tr>
  <tr id="sailfishnof27d">
    <td>7.1.1 (NOF27D, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nof27d-factory-be4efef1.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NOF27D]">Link</a></td>
    <td>be4efef17af09d268ab5d27a6d2ab51412e544b3f076f3d7a71e2b62df1f4eee</td>
  </tr>
  <tr id="sailfishn2g47e">
    <td>7.1.2 (N2G47E, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-n2g47e-factory-00a46e7e.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [N2G47E]">Link</a></td>
    <td>00a46e7ec5e000a18d17b07a348933b00eefc078c934dc726917c0fd92bebbe4</td>
  </tr>
  <tr id="sailfishn2g47j">
    <td>7.1.2 (N2G47J, Apr 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-n2g47j-factory-0a166464.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [N2G47J]">Link</a></td>
    <td>0a1664643d721ebb6235b291ad6d2ce77c01286dfbd63469b0f43b331ab64bb1</td>
  </tr>
  <tr id="sailfishnhg47k">
    <td>7.1.2 (NHG47K, Apr 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nhg47k-factory-59f23c7a.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NHG47K]">Link</a></td>
    <td>59f23c7a6e672337c4a5e4b98f240de63db7f2d161c08d05cf23ca92c31114c9</td>
  </tr>
  <tr id="sailfishn2g47o">
    <td>7.1.2 (N2G47O, May 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-n2g47o-factory-f2bc8024.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [N2G47O]">Link</a></td>
    <td>f2bc8024b015fdf1e79d0ae3da187cb0c371c7fd5a24e384abe75a0c7c1bdb41</td>
  </tr>
  <tr id="sailfishn2g47t">
    <td>7.1.2 (N2G47T, May 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-n2g47t-factory-fecae045.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [N2G47T]">Link</a></td>
    <td>fecae045bc1444880a2325207a25780770581eedf931c3a9c01aa46b1a670c68</td>
  </tr>
  <tr id="sailfishnhg47l">
    <td>7.1.2 (NHG47L, May 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nhg47l-factory-509076ee.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NHG47L]">Link</a></td>
    <td>509076eee8f730c1d3fa950158fbb55478db69f483fcde94c1e2e0f5a3685307</td>
  </tr>
  <tr id="sailfishnhg47n">
    <td>7.1.2 (NHG47N, Jun 2017, NHG47N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nhg47n-factory-5cea9f91.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NHG47N]">Link</a></td>
    <td>5cea9f9192c66266aee9c3b3d4004798323f6d051e209c7b87a2f2f76c35ac6c</td>
  </tr>
  <tr id="sailfishnjh34c">
    <td>7.1.2 (NJH34C, Jun 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-njh34c-factory-3158e0a2.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NJH34C]">Link</a></td>
    <td>3158e0a296be4677ae02c6d8b6b4ec722975dd07915efa0e62acd6a2eebb22a4</td>
  </tr>
  <tr id="sailfishnjh47b">
    <td>7.1.2 (NJH47B, Jun 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-njh47b-factory-1b1673a3.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NJH47B]">Link</a></td>
    <td>1b1673a3baa0e1d44c0da04323c40f71b7501ee3e83c43c5eee01633075ce61f</td>
  </tr>
  <tr id="sailfishnkg47l">
    <td>7.1.2 (NKG47L, Jun 2017, T-Mobile, Fi carriers, and Rogers)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nkg47l-factory-2a584648.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NKG47L]">Link</a></td>
    <td>2a584648a6f9ecc17309e290e69121b1547fe5e2b25d9c74abb898f817c54a55</td>
  </tr>
  <tr id="sailfishnhg47o">
    <td>7.1.2 (NHG47O, Jul 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nhg47o-factory-17c5ea14.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NHG47O]">Link</a></td>
    <td>17c5ea14e8b9b984d37ea03ee9af11263574b071f21cac219d1ae2ec51f9fa05</td>
  </tr>
  <tr id="sailfishnjh47d">
    <td>7.1.2 (NJH47D, Jul 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-njh47d-factory-953f6c69.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NJH47D]">Link</a></td>
    <td>953f6c699769cd123398185570047182334da19dee235e178a523d449e4e9c4a</td>
  </tr>
  <tr id="sailfishnkg47m">
    <td>7.1.2 (NKG47M, Jul 2017, T-Mobile, Fi carriers)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nkg47m-factory-713b6613.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NKG47M]">Link</a></td>
    <td>713b66132e92bb8c5ced2282628998de9d5835a1d0bfd6d74a15312bdb5d5349</td>
  </tr>
  <tr id="sailfishnzh54b">
    <td>7.1.2 (NZH54B, Jul 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nzh54b-factory-087eff7b.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NZH54B]">Link</a></td>
    <td>087eff7b428a4624ed4fc0bb51896b324892b625ad7bef03a0428ea38448a628</td>
  </tr>
  <tr id="sailfishnhg47q">
    <td>7.1.2 (NHG47Q, Aug 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nhg47q-factory-135beab7.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NHG47Q]">Link</a></td>
    <td>135beab7f55a7f9fcf5ae3384d0e79bfb3b39fbd963dc836d3b61dbf23dab8ae</td>
  </tr>
  <tr id="sailfishnjh47f">
    <td>7.1.2 (NJH47F, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-njh47f-factory-6fd9b2c4.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NJH47F]">Link</a></td>
    <td>6fd9b2c42ebbde474fff37765b90c8b688128cda24b2fffbeb46523a5acdfa14</td>
  </tr>
  <tr id="sailfishnkg47s">
    <td>7.1.2 (NKG47S, Aug 2017, T-Mobile, Fi carriers, and Rogers)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nkg47s-factory-f4b60f10.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NKG47S]">Link</a></td>
    <td>f4b60f104d33fed036efb00d33125bbf672b01b0a53f8a87b84836ed7959efb7</td>
  </tr>
  <tr id="sailfishnzh54d">
    <td>7.1.2 (NZH54D, Aug 2017, Deutsche Telekom)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-nzh54d-factory-127f0583.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [NZH54D]">Link</a></td>
    <td>127f058367fa854002e6fd4221cfbcdc748398b122a2b39dc5cad7aa9e902be3</td>
  </tr>
  <tr id="sailfishopr6.170623.011">
    <td>8.0.0 (OPR6.170623.011, Aug 2017, Bell, Telus, Telstra, TMO, Sprint, USCC, Rogers/Fido)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opr6.170623.011-factory-0d712594.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPR6.170623.011]">Link</a></td>
    <td>0d71259400371b8da44e6300324dbd6cbe26d6ae2641745becab9d7d1607e9db</td>
  </tr>
  <tr id="sailfishopr6.170623.012">
    <td>8.0.0 (OPR6.170623.012, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opr6.170623.012-factory-8ada9373.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPR6.170623.012]">Link</a></td>
    <td>8ada9373e6f86cac20023bd6c7889edb0449fc7085913d1e45f8a1491b17942c</td>
  </tr>
  <tr id="sailfishopr1.170623.026">
    <td>8.0.0 (OPR1.170623.026, Sep 2017, Fi/Canada)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opr1.170623.026-factory-26d3f82f.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPR1.170623.026]">Link</a></td>
    <td>26d3f82f8f5bed5be4c3ca4ea8642ce58253ca753359ae2fc8a7835cc4730103</td>
  </tr>
  <tr id="sailfishopr3.170623.007">
    <td>8.0.0 (OPR3.170623.007, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opr3.170623.007-factory-6a2629ba.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPR3.170623.007]">Link</a></td>
    <td>6a2629bab74c58b769403f1f25fd81ea64bdfbf6fc30281f2d9c2fb95a4e6bb7</td>
  </tr>
  <tr id="sailfishopr1.170623.027">
    <td>8.0.0 (OPR1.170623.027, Oct 2017, Fi/Canada)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opr1.170623.027-factory-87caffce.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPR1.170623.027]">Link</a></td>
    <td>87caffce63fcf8af3e20f95831fda86fd311a551fab666e0364e0f86f7d33a6b</td>
  </tr>
  <tr id="sailfishopr3.170623.008">
    <td>8.0.0 (OPR3.170623.008, Oct 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opr3.170623.008-factory-bb8bb3a3.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPR3.170623.008]">Link</a></td>
    <td>bb8bb3a3f81dbb5ea19cc16d9244c089146bd9f4653f9771e0add8b130c19f1e</td>
  </tr>
  <tr id="sailfishopr1.170623.032">
    <td>8.0.0 (OPR1.170623.032, Nov 2017, Fi/Canada)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opr1.170623.032-factory-e011ef43.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPR1.170623.032]">Link</a></td>
    <td>e011ef434ae32e24f14c19d83a859ed76a156209ba4552c393af38f5b1f3efd6</td>
  </tr>
  <tr id="sailfishopr3.170623.013">
    <td>8.0.0 (OPR3.170623.013, Nov 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opr3.170623.013-factory-bdc49b40.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPR3.170623.013]">Link</a></td>
    <td>bdc49b40d4a45b376e86c435487160d54a4f94baff00862c1e579ec60c9d5be3</td>
  </tr>
  <tr id="sailfishopm1.171019.011">
    <td>8.1.0 (OPM1.171019.011, Dec 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opm1.171019.011-factory-56d15350.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPM1.171019.011]">Link</a></td>
    <td>56d15350a2c54960b149fc8a080547f17e1c4bba4da89bb03f6c634746ca6318</td>
  </tr>
  <tr id="sailfishopm1.171019.012">
    <td>8.1.0 (OPM1.171019.012, Jan 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opm1.171019.012-factory-49ed1aec.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPM1.171019.012]">Link</a></td>
    <td>49ed1aec7de3bd002340a9db6d19903f0a3e8c8c94b21a2efbfabea8b94e5dc6</td>
  </tr>
  <tr id="sailfishopm1.171019.014">
    <td>8.1.0 (OPM1.171019.014, Jan 2018, O2/UK only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opm1.171019.014-factory-32322b4c.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPM1.171019.014]">Link</a></td>
    <td>32322b4cf384d2f77963385afd713e87d1cd40b398c6532ba39c806aec181f10</td>
  </tr>
  <tr id="sailfishopm1.171019.016">
    <td>8.1.0 (OPM1.171019.016, Feb 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opm1.171019.016-factory-8a6591cc.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPM1.171019.016]">Link</a></td>
    <td>8a6591cc28c420e779e881f46b725446bea2dc0760380465484a7976df796a19</td>
  </tr>
  <tr id="sailfishopm1.171019.021">
    <td>8.1.0 (OPM1.171019.021, Mar 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opm1.171019.021-factory-68d3b69a.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPM1.171019.021]">Link</a></td>
    <td>68d3b69a17a4f4bc0aea85ffc7db69b4103f7e5ac7568d0469a6a389927df407</td>
  </tr>
  <tr id="sailfishopm2.171019.029">
    <td>8.1.0 (OPM2.171019.029, Apr 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opm2.171019.029-factory-bee9592c.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPM2.171019.029]">Link</a></td>
    <td>bee9592ca8e5863f54e42dcba3102f44caaa68176cb4d721d3e57872a70384e7</td>
  </tr>
  <tr id="sailfishopm4.171019.016.b1">
    <td>8.1.0 (OPM4.171019.016.B1, May 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opm4.171019.016.b1-factory-68c3a77d.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPM4.171019.016.B1]">Link</a></td>
    <td>68c3a77dd68f2694e312507e90f8af6b7b32b33bf273ecd1def159850bfa8d2c</td>
  </tr>
  <tr id="sailfishopm4.171019.021.d1">
    <td>8.1.0 (OPM4.171019.021.D1, Jun 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opm4.171019.021.d1-factory-e2315135.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPM4.171019.021.D1]">Link</a></td>
    <td>e23151353bfeb8fc400ad5bf99c34136e2a6356343b68307d66826b0f18e0840</td>
  </tr>
  <tr id="sailfishopm4.171019.021.p1">
    <td>8.1.0 (OPM4.171019.021.P1, Jul 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-opm4.171019.021.p1-factory-0bcf4315.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [OPM4.171019.021.P1]">Link</a></td>
    <td>0bcf4315bcbd2dfe8878b00c778833ec61ddfdd156f33729fa02318f0317016a</td>
  </tr>
  <tr id="sailfishppr1.180610.009">
    <td>9.0.0 (PPR1.180610.009, Aug 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-ppr1.180610.009-factory-a945cab8.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PPR1.180610.009]">Link</a></td>
    <td>a945cab87553f7010764c2ea14745d3ef5aa7780e6d77c04babcc1787fac99b9</td>
  </tr>
  <tr id="sailfishppr1.180610.010">
    <td>9.0.0 (PPR1.180610.010, Aug 2018, Telus)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-ppr1.180610.010-factory-94ca0106.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PPR1.180610.010]">Link</a></td>
    <td>94ca010620ff958fdcf7d5da2bcdba1c00636e9f2247889cc516355a674ccde8</td>
  </tr>
  <tr id="sailfishppr1.180905.003">
    <td>9.0.0 (PPR1.180905.003, Sep 2018, Telus)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-ppr1.180905.003-factory-5b219c2e.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PPR1.180905.003]">Link</a></td>
    <td>5b219c2e767532a3f03a57698e4b82a0b845b03cfb521908c8e67697aab3928a</td>
  </tr>
  <tr id="sailfishppr2.180905.006">
    <td>9.0.0 (PPR2.180905.006, Sep 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-ppr2.180905.006-factory-bad3cb18.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PPR2.180905.006]">Link</a></td>
    <td>bad3cb1809c9bdf451149ce9d0db79d76a84cc3a1fb3602df485b55664d3d60c</td>
  </tr>
  <tr id="sailfishppr2.180905.006.a1">
    <td>9.0.0 (PPR2.180905.006.A1, Sep 2018, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-ppr2.180905.006.a1-factory-b063909b.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PPR2.180905.006.A1]">Link</a></td>
    <td>b063909b211beea28e6879a12db1dade1eb4c007900082c10ea160f15c6feae7</td>
  </tr>
  <tr id="sailfishppr1.181005.003">
    <td>9.0.0 (PPR1.181005.003, Oct 2018, Telus Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-ppr1.181005.003-factory-15fafd9d.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PPR1.181005.003]">Link</a></td>
    <td>15fafd9ddcb3c614d57453061d6ce2188b83daba008373b64b68bc5476a6a6b1</td>
  </tr>
  <tr id="sailfishppr2.181005.003">
    <td>9.0.0 (PPR2.181005.003, Oct 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-ppr2.181005.003-factory-727c51f5.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PPR2.181005.003]">Link</a></td>
    <td>727c51f523fda0fbff4f7950b691c43e7ebe791e4bc54a00c7d111e3789d3fc4</td>
  </tr>
  <tr id="sailfishppr1.181005.003.a1">
    <td>9.0.0 (PPR1.181005.003.A1, Nov 2018, Telus Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-ppr1.181005.003.a1-factory-6a2c3b69.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PPR1.181005.003.A1]">Link</a></td>
    <td>6a2c3b69a43f93e576f953d7c8368648bd26f7d23667556a65af40282a72f7af</td>
  </tr>
  <tr id="sailfishppr2.181005.003.a1">
    <td>9.0.0 (PPR2.181005.003.A1, Nov 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-ppr2.181005.003.a1-factory-dec6298c.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PPR2.181005.003.A1]">Link</a></td>
    <td>dec6298c7893c8a24599a764ce4ea41d4f5707ba4d69024c57a5b37b3e3c0975</td>
  </tr>
  <tr id="sailfishpq1a.181205.002.a1">
    <td>9.0.0 (PQ1A.181205.002.A1, Dec 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-pq1a.181205.002.a1-factory-6a61ff63.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PQ1A.181205.002.A1]">Link</a></td>
    <td>6a61ff636875d6dd382ffb9ce3103ebc85b55754c7926179e03a8525833144ee</td>
  </tr>
  <tr id="sailfishpq1a.190105.004">
    <td>9.0.0 (PQ1A.190105.004, Jan 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-pq1a.190105.004-factory-fc5db1d4.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PQ1A.190105.004]">Link</a></td>
    <td>fc5db1d45784659f8746e6895a13dddc4550d3af0b61925313b65c7bd503cc7e</td>
  </tr>
  <tr id="sailfishpq2a.190205.003">
    <td>9.0.0 (PQ2A.190205.003, Feb 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-pq2a.190205.003-factory-164a7269.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PQ2A.190205.003]">Link</a></td>
    <td>164a72699b7efea606ebedf573fa7b4bae1dcbdadede220483383ce329553efe</td>
  </tr>
  <tr id="sailfishpq2a.190305.002">
    <td>9.0.0 (PQ2A.190305.002, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-pq2a.190305.002-factory-73582e64.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PQ2A.190305.002]">Link</a></td>
    <td>73582e64a61bd909c460b3a6687d6c9d2d8c1ba0ea18250c1ec7643714fdae6b</td>
  </tr>
  <tr id="sailfishpq2a.190405.003">
    <td>9.0.0 (PQ2A.190405.003, Apr 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-pq2a.190405.003-factory-3b16bbc7.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PQ2A.190405.003]">Link</a></td>
    <td>3b16bbc758cc201b276157a9852e49c19d046f3d9a9891aa96f7cc84571c03de</td>
  </tr>
  <tr id="sailfishpq3a.190505.001">
    <td>9.0.0 (PQ3A.190505.001, May 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-pq3a.190505.001-factory-f3d2032d.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PQ3A.190505.001]">Link</a></td>
    <td>f3d2032d0862961a1712445226f942f7f430851fbbac045b724cffafaa5c6e83</td>
  </tr>
  <tr id="sailfishpq3a.190605.003">
    <td>9.0.0 (PQ3A.190605.003, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-pq3a.190605.003-factory-3128c984.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PQ3A.190605.003]">Link</a></td>
    <td>3128c984ab63e16219113c4df7b03bdec6afacd8a6b5c0e46daac67c0237671f</td>
  </tr>
  <tr id="sailfishpq3a.190705.001">
    <td>9.0.0 (PQ3A.190705.001, Jul 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-pq3a.190705.001-factory-7f9ff7f7.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PQ3A.190705.001]">Link</a></td>
    <td>7f9ff7f7fd447ecb9a3724878c71afc8ea64969cb085b900ce6827da3cc97a1a</td>
  </tr>
  <tr id="sailfishpq3a.190801.002">
    <td>9.0.0 (PQ3A.190801.002, Aug 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-pq3a.190801.002-factory-029a3376.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [PQ3A.190801.002]">Link</a></td>
    <td>029a3376237220354c6bddc98a38a893976fb280a42b8c091200d5527ccbcd45</td>
  </tr>
  <tr id="sailfishqp1a.190711.019">
    <td>10.0.0 (QP1A.190711.019, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-qp1a.190711.019-factory-83a26262.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [QP1A.190711.019]">Link</a></td>
    <td>83a2626261bf21d208376677db969e2920cd6d7814f04b4673035b68020dd9c2</td>
  </tr>
  <tr id="sailfishqp1a.190711.020">
    <td>10.0.0 (QP1A.190711.020, Sep 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-qp1a.190711.020-factory-0bb95222.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [QP1A.190711.020]">Link</a></td>
    <td>0bb952229c861826b799084be63d834b63d227f22fb3d26a470d5d9b52b6d662</td>
  </tr>
  <tr id="sailfishqp1a.191005.007.a1">
    <td>10.0.0 (QP1A.191005.007.A1, Oct 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sailfish-qp1a.191005.007.a1-factory-78c6703e.zip" class="gc-analytics-event" data-category="Android Images" data-label="sailfish for Pixel [QP1A.191005.007.A1]">Link</a></td>
    <td>78c6703ea4473ed65c51d6e258bb67368962bd13aad3975db08b42c7b8d49cb0</td>
  </tr>
</tbody></table></div>

<h2 id="ryu" is-upgraded="">"ryu" for Pixel C</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="ryumxb48j">
    <td>6.0.1 (MXB48J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-mxb48j-factory-ce6d5a7b.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [MXB48J]">Link</a></td>
    <td>ce6d5a7bdfd61f2fe93b0e77d9b67f19a4e78825221c45c08ab1a6836b178de6</td>
  </tr>
  <tr id="ryumxb48k">
    <td>6.0.1 (MXB48K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-mxb48k-factory-e13a6b01.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [MXB48K]">Link</a></td>
    <td>e13a6b012eb407fbdddfef2a5b482a1c12b28db6ee4250bc61fe0d2d835f6508</td>
  </tr>
  <tr id="ryumxb48t">
    <td>6.0.1 (MXB48T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-mxb48t-factory-5bf811b5.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [MXB48T]">Link</a></td>
    <td>5bf811b544432444d47949d18620644bfcb857b017913afea36fbd4a9cb6831a</td>
  </tr>
  <tr id="ryumxc14g">
    <td>6.0.1 (MXC14G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-mxc14g-factory-49149866.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [MXC14G]">Link</a></td>
    <td>491498662e87df1398bed2ac11f253c97acd16f275f35d61f254c49b02c2f34d</td>
  </tr>
  <tr id="ryum5c14j">
    <td>6.0.1 (M5C14J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-m5c14j-factory-ee1c5509.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [M5C14J]">Link</a></td>
    <td>ee1c55092fa4f2ba3eef69576b556f23af6b752d38c05d485fd972bfa70f31a1</td>
  </tr>
  <tr id="ryumxc89f">
    <td>6.0.1 (MXC89F)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-mxc89f-factory-de76375c.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [MXC89F]">Link</a></td>
    <td>de76375c3dc79338e97f67fa3092e502d9fc960cd296ed8be4582aa14d79b492</td>
  </tr>
  <tr id="ryumxc89h">
    <td>6.0.1 (MXC89H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-mxc89h-factory-11161f52.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [MXC89H]">Link</a></td>
    <td>11161f523b4305d5ca81e7a7fe3da7bc7ec718598801fe41f7cdfb59544a219a</td>
  </tr>
  <tr id="ryumxc89k">
    <td>6.0.1 (MXC89K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-mxc89k-factory-9a5ae97e.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [MXC89K]">Link</a></td>
    <td>9a5ae97e093abda91131dd9337b40d49f866da58b60f34c06145d6100f56c5ec</td>
  </tr>
  <tr id="ryumxc89l">
    <td>6.0.1 (MXC89L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-mxc89l-factory-1f9a5fcb.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [MXC89L]">Link</a></td>
    <td>1f9a5fcbf9d91e79720bcaebd2873116090065b05f8ece1f764c64f4b781e791</td>
  </tr>
  <tr id="ryunrd90m">
    <td>7.0.0 (NRD90M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-nrd90m-factory-29233f1a.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [NRD90M]">Link</a></td>
    <td>29233f1ac43e9309d6c8ee6273682a7ca172f129a062d611eb9f77c6e7eb5e3a</td>
  </tr>
  <tr id="ryunrd90r">
    <td>7.0.0 (NRD90R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-nrd90r-factory-843758b3.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [NRD90R]">Link</a></td>
    <td>843758b3c5bc6ef0e73102b13c1a7e33a0b2645c39c4966ade312a5d2e6574ae</td>
  </tr>
  <tr id="ryunrd91d">
    <td>7.0.0 (NRD91D, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-nrd91d-factory-13a00ca0.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [NRD91D]">Link</a></td>
    <td>13a00ca040924b6101e9a6b4f9ba7327ad72364f7d4e6b27498bdf0a651a9fa7</td>
  </tr>
  <tr id="ryunrd91n">
    <td>7.0.0 (NRD91N, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-nrd91n-factory-5abda8a4.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [NRD91N]">Link</a></td>
    <td>5abda8a4f6fb35f1aa3d2fc5b347e6bf0b84f2747572ac4dbd7d9c902bb64694</td>
  </tr>
  <tr id="ryunmf26h">
    <td>7.1.1 (NMF26H, Dec 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-nmf26h-factory-52ad10d8.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [NMF26H]">Link</a></td>
    <td>52ad10d82325d9c36be9b79839d7397a4bedd94834f8281db31cb4e3ded48ccb</td>
  </tr>
  <tr id="ryun4f26i">
    <td>7.1.1 (N4F26I, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-n4f26i-factory-2aa98ca1.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [N4F26I]">Link</a></td>
    <td>2aa98ca14987da8229eca8210bc1c15b4fbba75abe25dfec0f4e8583af024d9a</td>
  </tr>
  <tr id="ryun4f26o">
    <td>7.1.1 (N4F26O, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-n4f26o-factory-307fc15e.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [N4F26O]">Link</a></td>
    <td>307fc15eac81233b93ced1bd87570c891ad0ca4290288e56cadd750d9f544e1d</td>
  </tr>
  <tr id="ryun4f26t">
    <td>7.1.1 (N4F26T, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-n4f26t-factory-d05202a0.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [N4F26T]">Link</a></td>
    <td>d05202a077105a822e3755049878bb11337481e42f7a0325470068275df1b7e2</td>
  </tr>
  <tr id="ryun2g47d">
    <td>7.1.2 (N2G47D, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-n2g47d-factory-191d8ea6.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [N2G47D]">Link</a></td>
    <td>191d8ea6b78033f8d9af290401a282345f2ac4cde7c2078e389482fb9230988d</td>
  </tr>
  <tr id="ryun2g47o">
    <td>7.1.2 (N2G47O, May 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-n2g47o-factory-7918a74f.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [N2G47O]">Link</a></td>
    <td>7918a74f901fbcade1ce7ee145f6685bf7c1a87d7cd57267972b07092c575024</td>
  </tr>
  <tr id="ryun2g47w">
    <td>7.1.2 (N2G47W, Jun 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-n2g47w-factory-45c8abfa.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [N2G47W]">Link</a></td>
    <td>45c8abfaef1af9255611f6a9f7d57a2a7ce78738e19e2a20be4699d4b9487104</td>
  </tr>
  <tr id="ryun2g48b">
    <td>7.1.2 (N2G48B, Jul 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-n2g48b-factory-fa17d973.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [N2G48B]">Link</a></td>
    <td>fa17d9734da41b154a3592feb2f36313da60badcca6a8903a683e2ebc1920517</td>
  </tr>
  <tr id="ryun2g48c">
    <td>7.1.2 (N2G48C, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-n2g48c-factory-0bc0ee15.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [N2G48C]">Link</a></td>
    <td>0bc0ee15ad02bd3bd222c7b0abc6f518512978c79470e5addb5f5f45646f2c0d</td>
  </tr>
  <tr id="ryuopr6.170623.010">
    <td>8.0.0 (OPR6.170623.010, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opr6.170623.010-factory-81a1479d.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPR6.170623.010]">Link</a></td>
    <td>81a1479d62eddc5657c6b496a5581bafe07265b61f7e0c3b259430fcc7119758</td>
  </tr>
  <tr id="ryuopr1.170623.026">
    <td>8.0.0 (OPR1.170623.026, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opr1.170623.026-factory-e27ff2c8.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPR1.170623.026]">Link</a></td>
    <td>e27ff2c88f88b13d1e431321b27b1bcf7fe6552c0644aba914ffea286e38ea0e</td>
  </tr>
  <tr id="ryuopr1.170623.027">
    <td>8.0.0 (OPR1.170623.027, Oct 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opr1.170623.027-factory-fde49df9.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPR1.170623.027]">Link</a></td>
    <td>fde49df968a67e51a3f36876af19820323e26949a49d3884f53aacd4df64b344</td>
  </tr>
  <tr id="ryuopr1.170623.032">
    <td>8.0.0 (OPR1.170623.032, Nov 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opr1.170623.032-factory-020f1cf9.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPR1.170623.032]">Link</a></td>
    <td>020f1cf911cc78dc36162b3bdb68ec6dd965ad3a92e9f4a78c7a519d18470075</td>
  </tr>
  <tr id="ryuopm1.171019.011">
    <td>8.1.0 (OPM1.171019.011, Dec 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm1.171019.011-factory-ccc99463.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM1.171019.011]">Link</a></td>
    <td>ccc99463d567d42e2d2a4e65be64670fa28d1f4cd9fcf1e6616ad6a4b71e65ec</td>
  </tr>
  <tr id="ryuopm1.171019.015">
    <td>8.1.0 (OPM1.171019.015, Jan 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm1.171019.015-factory-64c65be2.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM1.171019.015]">Link</a></td>
    <td>64c65be241b20f085c554c09ccc87cb10222ce7d96861558f14fabe9c8f50f7b</td>
  </tr>
  <tr id="ryuopm1.171019.016">
    <td>8.1.0 (OPM1.171019.016, Feb 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm1.171019.016-factory-fd9cb83e.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM1.171019.016]">Link</a></td>
    <td>fd9cb83e1fa9d9b5616d7662d44771a6fcea012abb4a86131544f975ea88babe</td>
  </tr>
  <tr id="ryuopm1.171019.022.a1">
    <td>8.1.0 (OPM1.171019.022.A1, Mar 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm1.171019.022.a1-factory-e5c762a1.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM1.171019.022.A1]">Link</a></td>
    <td>e5c762a178dc2194c86f7a5091b2302a44e6237aa99a7efd76b9cd97cee8bab4</td>
  </tr>
  <tr id="ryuopm1.171019.026">
    <td>8.1.0 (OPM1.171019.026, Apr 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm1.171019.026-factory-8f7df218.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM1.171019.026]">Link</a></td>
    <td>8f7df21829368e87123f55f8954f8b8edb52c0f77cb4a504c783dad7637dd8f4</td>
  </tr>
  <tr id="ryuopm4.171019.016.c1">
    <td>8.1.0 (OPM4.171019.016.C1, May 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm4.171019.016.c1-factory-1fa14065.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM4.171019.016.C1]">Link</a></td>
    <td>1fa1406541eac02e3f422ec03d48af2b352564e21efed50b9c62e93d622e517e</td>
  </tr>
  <tr id="ryuopm4.171019.021.d1">
    <td>8.1.0 (OPM4.171019.021.D1, Jun 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm4.171019.021.d1-factory-d198e485.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM4.171019.021.D1]">Link</a></td>
    <td>d198e485ca4485f4ebef484d82dbb01072ad0890feaf9ea6c03a7bcd33cc2435</td>
  </tr>
  <tr id="ryuopm4.171019.021.n1">
    <td>8.1.0 (OPM4.171019.021.N1, Jul 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm4.171019.021.n1-factory-1f31fdce.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM4.171019.021.N1]">Link</a></td>
    <td>1f31fdce8d6f941ceef09dcfe81e3a65ef8eb33c857c1f80ef3af6c204c364a9</td>
  </tr>
  <tr id="ryuopm4.171019.021.y1">
    <td>8.1.0 (OPM4.171019.021.Y1, Aug 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm4.171019.021.y1-factory-02bcca94.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM4.171019.021.Y1]">Link</a></td>
    <td>02bcca943089ca31e9a83c4500fd9d37f7b7c584230fa2130294fcdc33f08c81</td>
  </tr>
  <tr id="ryuopm4.171019.021.z1">
    <td>8.1.0 (OPM4.171019.021.Z1, Sep 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm4.171019.021.z1-factory-5caf896d.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM4.171019.021.Z1]">Link</a></td>
    <td>5caf896d79430f4a12dd1cb937bbed7b1557456875543cd6d587e999e2e9b91c</td>
  </tr>
  <tr id="ryuopm8.181005.003">
    <td>8.1.0 (OPM8.181005.003, Oct 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.181005.003-factory-d5eea995.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.181005.003]">Link</a></td>
    <td>d5eea99520bf396c85648b1cc4e6bba73b9943c21e17425bc2621cc5309db04b</td>
  </tr>
  <tr id="ryuopm8.181105.002">
    <td>8.1.0 (OPM8.181105.002, Nov 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.181105.002-factory-fa8f00b5.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.181105.002]">Link</a></td>
    <td>fa8f00b5d15ae705b22acf65291dd1cc28c72fca61f60e2e6dd38f4aab705f56</td>
  </tr>
  <tr id="ryuopm8.181205.001">
    <td>8.1.0 (OPM8.181205.001, Dec 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.181205.001-factory-11eb366b.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.181205.001]">Link</a></td>
    <td>11eb366bfa1eddeda13f2610c88df33742e931b9783e078992b13c447e5e1d65</td>
  </tr>
  <tr id="ryuopm8.190105.002">
    <td>8.1.0 (OPM8.190105.002, Jan 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.190105.002-factory-9f1e2867.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.190105.002]">Link</a></td>
    <td>9f1e2867ac928fcd96e6ed176ffea95bc27c7b84402c9875c47e51c05acf2e30</td>
  </tr>
  <tr id="ryuopm8.190205.001">
    <td>8.1.0 (OPM8.190205.001, Feb 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.190205.001-factory-84f16195.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.190205.001]">Link</a></td>
    <td>84f16195106f3c282795178784916012bda76bdf3fc454262c07793479a7667c</td>
  </tr>
  <tr id="ryuopm8.190305.001">
    <td>8.1.0 (OPM8.190305.001, Mar 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.190305.001-factory-0d59fffd.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.190305.001]">Link</a></td>
    <td>0d59fffd3d3ba68d79098cc9f5347449ee9b1cb336fcf615e3515ae7e62885f4</td>
  </tr>
  <tr id="ryuopm8.190405.001">
    <td>8.1.0 (OPM8.190405.001, Apr 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.190405.001-factory-08674d7b.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.190405.001]">Link</a></td>
    <td>08674d7bcb287541ebddb597e4abbade0bb7d059f6a048a5b8c9b1f53524faba</td>
  </tr>
  <tr id="ryuopm8.190505.001">
    <td>8.1.0 (OPM8.190505.001, May 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.190505.001-factory-d6019509.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.190505.001]">Link</a></td>
    <td>d60195096f4507e88d17c572db7fba9081088b5597f83d6494e5025de0118a6f</td>
  </tr>
  <tr id="ryuopm8.190605.003">
    <td>8.1.0 (OPM8.190605.003, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.190605.003-factory-4548e81b.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.190605.003]">Link</a></td>
    <td>4548e81b985d4870b850a26eb0cee211b026068f1974781df1f2249e0866c857</td>
  </tr>
  <tr id="ryuopm8.190605.005">
    <td>8.1.0 (OPM8.190605.005, Jun 2019)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/ryu-opm8.190605.005-factory-25b457f3.zip" class="gc-analytics-event" data-category="Android Images" data-label="ryu for Pixel C [OPM8.190605.005]">Link</a></td>
    <td>25b457f38b549d7195b8b1b09b77c5fbf02e249d4e7789ae71fe8070036d0d8c</td>
  </tr>
</tbody></table></div>

<h2 id="angler" is-upgraded="">"angler" for Nexus 6P</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="anglermda89d">
    <td>6.0.0 (MDA89D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mda89d-factory-9f001626.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MDA89D]">Link</a></td>
    <td>9f001626d37785a4845e2d61c53caaff839a31713062e49b29ede6b5fe807e68</td>
  </tr>
  <tr id="anglermdb08k">
    <td>6.0.0 (MDB08K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mdb08k-factory-46550886.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MDB08K]">Link</a></td>
    <td>4655088655f64e4f778adebe9e0ac8099447af643cf983262a95a1abf4401053</td>
  </tr>
  <tr id="anglermdb08l">
    <td>6.0.0 (MDB08L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mdb08l-factory-bb060be5.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MDB08L]">Link</a></td>
    <td>bb060be5690856a09325862c94c3568775034bc0c78678d6cdc2ea6dd77feb5d</td>
  </tr>
  <tr id="anglermdb08m">
    <td>6.0.0 (MDB08M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mdb08m-factory-5690aabf.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MDB08M]">Link</a></td>
    <td>5690aabf9b18d19ffff5949907eb123f15aff6cbfa31f67c1eeef0650a1fa1fe</td>
  </tr>
  <tr id="anglermmb29n">
    <td>6.0.0 (MMB29N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mmb29n-factory-63f8243f.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MMB29N]">Link</a></td>
    <td>63f8243f3bc4fed4638ce9bc943d989da34e73775de6efa1677dad37be3fa1b7</td>
  </tr>
  <tr id="anglermmb29m">
    <td>6.0.1 (MMB29M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mmb29m-factory-616cf265.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MMB29M]">Link</a></td>
    <td>616cf265c50f3960883f4c0e22b5e795defd8853cfdc83c61448054a06bf6a7f</td>
  </tr>
  <tr id="anglermmb29p">
    <td>6.0.1 (MMB29P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mmb29p-factory-ba26af97.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MMB29P]">Link</a></td>
    <td>ba26af977515fc9279f78aec766b6e1da33d3ecb8101985a46d7f35b5e7cde7a</td>
  </tr>
  <tr id="anglermmb29q">
    <td>6.0.1 (MMB29Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mmb29q-factory-24a6e02f.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MMB29Q]">Link</a></td>
    <td>24a6e02f2c3134a32e0d164d0163834595787faab48b07e92fc4a4a89d26e255</td>
  </tr>
  <tr id="anglermmb29v">
    <td>6.0.1 (MMB29V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mmb29v-factory-17366b60.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MMB29V]">Link</a></td>
    <td>17366b60a63f8d3a9844f7562ea04d1a4409a9ce908452316656d3a3c8207153</td>
  </tr>
  <tr id="anglermhc19i">
    <td>6.0.1 (MHC19I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mhc19i-factory-545ef106.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MHC19I]">Link</a></td>
    <td>545ef1061782108ad699b96a1f05a59c73eeed6662d8d6fe6448c796a1143752</td>
  </tr>
  <tr id="anglermhc19q">
    <td>6.0.1 (MHC19Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mhc19q-factory-e49fbdfd.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MHC19Q]">Link</a></td>
    <td>e49fbdfd9982787166b5b159861f9d41ba817b87c1ec43f8ec9eb02565d78689</td>
  </tr>
  <tr id="anglermtc19t">
    <td>6.0.1 (MTC19T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mtc19t-factory-095027d5.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MTC19T]">Link</a></td>
    <td>095027d58b891101167b85a0032998e720da588ceb0b4411c6b1c3f942d68e4c</td>
  </tr>
  <tr id="anglermtc19v">
    <td>6.0.1 (MTC19V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mtc19v-factory-b322694c.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MTC19V]">Link</a></td>
    <td>b322694cd8b4f2dfba77889dd9cc645b59e535c4c944816e35632261625f8771</td>
  </tr>
  <tr id="anglermtc19x">
    <td>6.0.1 (MTC19X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mtc19x-factory-ee8f6cd9.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MTC19X]">Link</a></td>
    <td>ee8f6cd94ce599d6b938ad055c7a1c333b9ef525acba63fc81fc7385bf167f0b</td>
  </tr>
  <tr id="anglermtc20f">
    <td>6.0.1 (MTC20F)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mtc20f-factory-4355fe06.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MTC20F]">Link</a></td>
    <td>4355fe06c7f4fe5a319838991bdef3381cf566253030f968e877f4003e4d5148</td>
  </tr>
  <tr id="anglermtc20l">
    <td>6.0.1 (MTC20L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-mtc20l-factory-b7864fdb.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [MTC20L]">Link</a></td>
    <td>b7864fdb261080ba1ab7126f7f2dee9e80fab088375677c51fb0347a52fb6179</td>
  </tr>
  <tr id="anglernrd90t">
    <td>7.0.0 (NRD90T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-nrd90t-factory-75edc1f7.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [NRD90T]">Link</a></td>
    <td>75edc1f7a52c81907a294530bcd1248cc821b627e22f97076c1ee31ea11de179</td>
  </tr>
  <tr id="anglernrd90u">
    <td>7.0.0 (NRD90U)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-nrd90u-factory-7c9b6a2b.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [NRD90U]">Link</a></td>
    <td>7c9b6a2b91be9cfad51e40cd43a9c82be9829a4af6d581c456802ec41017b4d9</td>
  </tr>
  <tr id="anglernbd90x">
    <td>7.0.0 (NBD90X, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-nbd90x-factory-4e17ed23.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [NBD90X]">Link</a></td>
    <td>4e17ed23bd461960996a32453d2d378ee3ac036b964bef68e5c1df55971a65af</td>
  </tr>
  <tr id="anglernbd91k">
    <td>7.0.0 (NBD91K, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-nbd91k-factory-6f206c95.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [NBD91K]">Link</a></td>
    <td>6f206c95da22ae17a26e5da22a14a09e676ded955ec401948493433c4b927fac</td>
  </tr>
  <tr id="anglernmf26f">
    <td>7.1.1 (NMF26F, Dec 2016. All carriers except Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-nmf26f-factory-ef607244.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [NMF26F]">Link</a></td>
    <td>ef60724457149b9db8ad9fcd4202e4f110d0541f8f2c9228ec07e0135a120315</td>
  </tr>
  <tr id="anglern4f26i">
    <td>7.1.1 (N4F26I, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n4f26i-factory-ff60a465.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N4F26I]">Link</a></td>
    <td>ff60a4656fcd7bc0cb051362d1733e876257e393685229bb698753b471081d75</td>
  </tr>
  <tr id="anglern4f26j">
    <td>7.1.1 (N4F26J, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n4f26j-factory-01874fd6.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N4F26J]">Link</a></td>
    <td>01874fd682f11ee513242fa5c75a15c52f97371b1c06a8795bf288fc913ef7bb</td>
  </tr>
  <tr id="anglern4f26o">
    <td>7.1.1 (N4F26O, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n4f26o-factory-c53f0a50.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N4F26O]">Link</a></td>
    <td>c53f0a502154f4e78884d6b39041a2a7adda89c928c3681e0d613a34b864ff13</td>
  </tr>
  <tr id="anglernuf26k">
    <td>7.1.1 (NUF26K, Feb 2017, Verizon Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-nuf26k-factory-bde381d4.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [NUF26K]">Link</a></td>
    <td>bde381d45306c6adfcbb0c14c5e0603b0230a1a983a2492b0117197efa263143</td>
  </tr>
  <tr id="anglern4f26t">
    <td>7.1.1 (N4F26T, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n4f26t-factory-50ddc702.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N4F26T]">Link</a></td>
    <td>50ddc7027f726f32a93d1035b95cdc56518b07edb3c0507e27edb41fcb0dc5a6</td>
  </tr>
  <tr id="anglernuf26n">
    <td>7.1.1 (NUF26N, Mar 2017, Verizon Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-nuf26n-factory-4612cdec.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [NUF26N]">Link</a></td>
    <td>4612cdec702583cc7ccd95b7c99ebe2b74338f6e2594468581bfad452e026e3b</td>
  </tr>
  <tr id="anglern4f26u">
    <td>7.1.1 (N4F26U, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n4f26u-factory-131d7b01.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N4F26U]">Link</a></td>
    <td>131d7b01edd691eede96c64a5911466b944e32929e156d8e5bec6841593af6fd</td>
  </tr>
  <tr id="anglern2g47h">
    <td>7.1.2 (N2G47H, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n2g47h-factory-f1111327.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N2G47H]">Link</a></td>
    <td>f1111327051062c28aa80a96a51f56b1897ecb619a7f3f09696a192420954fdc</td>
  </tr>
  <tr id="anglern2g47o">
    <td>7.1.2 (N2G47O, May 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n2g47o-factory-dc258043.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N2G47O]">Link</a></td>
    <td>dc258043828b0a6b96791011857eb8c1b82ae67496e433ebccbc516cd1db4a91</td>
  </tr>
  <tr id="anglern2g47w">
    <td>7.1.2 (N2G47W, Jun 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n2g47w-factory-bd87661a.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N2G47W]">Link</a></td>
    <td>bd87661ac3d16c7902abf9fc44b50606ff6cc8c90d0dca9364032d303e882ce4</td>
  </tr>
  <tr id="anglern2g48b">
    <td>7.1.2 (N2G48B, Jul 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n2g48b-factory-34c51cad.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N2G48B]">Link</a></td>
    <td>34c51cadceaa568bdf324d6e3a1788c837b4b9256c64565ee0f3869094974201</td>
  </tr>
  <tr id="anglern2g48c">
    <td>7.1.2 (N2G48C, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-n2g48c-factory-6a21e528.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [N2G48C]">Link</a></td>
    <td>6a21e52889246aee2be75479af1a684d4e1c78259dfc88a73a1e57e786cd771b</td>
  </tr>
  <tr id="angleropr6.170623.013">
    <td>8.0.0 (OPR6.170623.013, Aug 2017, Not for TMO/USCC/Fi)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opr6.170623.013-factory-a63b2f21.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPR6.170623.013]">Link</a></td>
    <td>a63b2f21ad07d7b163cdb0ff26b4d3aedfa3869462d4b86369dc35d5653895bb</td>
  </tr>
  <tr id="angleropr6.170623.019">
    <td>8.0.0 (OPR6.170623.019, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opr6.170623.019-factory-9fd72ad6.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPR6.170623.019]">Link</a></td>
    <td>9fd72ad64ea223f8578f7058c83864e8764706abaff8283b527249f6fe57af61</td>
  </tr>
  <tr id="angleropr5.170623.007">
    <td>8.0.0 (OPR5.170623.007, Oct 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opr5.170623.007-factory-b4c75d12.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPR5.170623.007]">Link</a></td>
    <td>b4c75d12530fcb7f92d4e0716296ad1e582e59f335f96c12d236d732c7a24803</td>
  </tr>
  <tr id="angleropr5.170623.011">
    <td>8.0.0 (OPR5.170623.011, Nov 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opr5.170623.011-factory-0e60ceb6.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPR5.170623.011]">Link</a></td>
    <td>0e60ceb689de1a430925188d7412f9fcfb2f3cfe25f33830f701a4644863f8ca</td>
  </tr>
  <tr id="angleropr5.170623.014">
    <td>8.0.0 (OPR5.170623.014, Dec 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opr5.170623.014-factory-9cce48d8.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPR5.170623.014]">Link</a></td>
    <td>9cce48d868ea2cfe39aca6ef17d914bec503fccdb20c2d4d9b205cec1dc62ca4</td>
  </tr>
  <tr id="angleropm1.171019.011">
    <td>8.1.0 (OPM1.171019.011, Dec 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm1.171019.011-factory-39448337.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM1.171019.011]">Link</a></td>
    <td>39448337f1716a7e097a9b32655b826ca308a2adb0182263f086a1e284d900df</td>
  </tr>
  <tr id="angleropm3.171019.013">
    <td>8.1.0 (OPM3.171019.013, Jan 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm3.171019.013-factory-3204625a.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM3.171019.013]">Link</a></td>
    <td>3204625a24c0569e7e13d44edef656fcf1d35816b2854f38c6ffebbdcf826a53</td>
  </tr>
  <tr id="angleropm5.171019.014">
    <td>8.1.0 (OPM5.171019.014, Jan 2018, Softbank)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm5.171019.014-factory-a96bc15a.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM5.171019.014]">Link</a></td>
    <td>a96bc15a458a77441348da3caf72d2d179f4793bad6347f105097fe01e139af6</td>
  </tr>
  <tr id="angleropm3.171019.014">
    <td>8.1.0 (OPM3.171019.014, Feb 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm3.171019.014-factory-75d6fd94.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM3.171019.014]">Link</a></td>
    <td>75d6fd94c97b914dd76605d35b46526250ae8a52745d50e0ab2e4395ac5d0584</td>
  </tr>
  <tr id="angleropm5.171019.015">
    <td>8.1.0 (OPM5.171019.015, Feb 2018, Softbank)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm5.171019.015-factory-1e006a8d.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM5.171019.015]">Link</a></td>
    <td>1e006a8d17ebc3ca22d17491f2dcc1e47444eb1d45c9ff56233ced3924bd2ec9</td>
  </tr>
  <tr id="angleropm3.171019.016">
    <td>8.1.0 (OPM3.171019.016, Mar 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm3.171019.016-factory-08de5265.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM3.171019.016]">Link</a></td>
    <td>08de5265eb9519b313e55ba2df526b9f02496b91b869c3effa3184de43af2cf6</td>
  </tr>
  <tr id="angleropm5.171019.017">
    <td>8.1.0 (OPM5.171019.017, Mar 2018, Softbank)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm5.171019.017-factory-64398f10.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM5.171019.017]">Link</a></td>
    <td>64398f101c8ba3a5ca72148a60cdd7212d10f95a5dcac2069322bfd37e5fe89b</td>
  </tr>
  <tr id="angleropm3.171019.019">
    <td>8.1.0 (OPM3.171019.019, Apr 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm3.171019.019-factory-e48da4e0.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM3.171019.019]">Link</a></td>
    <td>e48da4e058f987600da708513bc31d334351577bd1b47204ee6cb4b79afed557</td>
  </tr>
  <tr id="angleropm5.171019.019">
    <td>8.1.0 (OPM5.171019.019, Apr 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm5.171019.019-factory-e6191337.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM5.171019.019]">Link</a></td>
    <td>e6191337ae977b5a1bac32cbafae6c5edf9765d3f80f7693c5ce16d60b6fc628</td>
  </tr>
  <tr id="angleropm2.171019.029.a1">
    <td>8.1.0 (OPM2.171019.029.A1, May 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm2.171019.029.a1-factory-bf17e552.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM2.171019.029.A1]">Link</a></td>
    <td>bf17e55271cbcf6235f5772cf6db06af6db4003b0b3873d6bc5517e3f8024815</td>
  </tr>
  <tr id="angleropm6.171019.030.b1">
    <td>8.1.0 (OPM6.171019.030.B1, Jun 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm6.171019.030.b1-factory-ab13a98b.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM6.171019.030.B1]">Link</a></td>
    <td>ab13a98be182f7046a98fbaf657b1825ced93e14ded2b0fbaf2d0e8fc422f17c</td>
  </tr>
  <tr id="angleropm6.171019.030.e1">
    <td>8.1.0 (OPM6.171019.030.E1, Jul 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm6.171019.030.e1-factory-1abcb2f1.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM6.171019.030.E1]">Link</a></td>
    <td>1abcb2f11fa3ad926b140173693499feb70db9d5ee6ece05c9c902aae1017f64</td>
  </tr>
  <tr id="angleropm6.171019.030.h1">
    <td>8.1.0 (OPM6.171019.030.H1, Aug 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm6.171019.030.h1-factory-00138df6.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM6.171019.030.H1]">Link</a></td>
    <td>00138df633bacd55beb96a1211863b849f08c145265defcd9638569ef07010bc</td>
  </tr>
  <tr id="angleropm6.171019.030.k1">
    <td>8.1.0 (OPM6.171019.030.K1, Sep 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm6.171019.030.k1-factory-adc4f069.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM6.171019.030.K1]">Link</a></td>
    <td>adc4f0698eb760d5fc76b8c4d8d72727600975320eeb4f0d19555decba066d20</td>
  </tr>
  <tr id="angleropm7.181005.003">
    <td>8.1.0 (OPM7.181005.003, Oct 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm7.181005.003-factory-42c955a4.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM7.181005.003]">Link</a></td>
    <td>42c955a4869bb3e3be569aefd4c7f03677fdce7908c314d8bb407b86550a43b6</td>
  </tr>
  <tr id="angleropm7.181105.004">
    <td>8.1.0 (OPM7.181105.004, Nov 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm7.181105.004-factory-41baa917.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM7.181105.004]">Link</a></td>
    <td>41baa917b4ca6034a36c30d20540b21b81b4d91bb2b3db01a24af83ead797798</td>
  </tr>
  <tr id="angleropm7.181205.001">
    <td>8.1.0 (OPM7.181205.001, Dec 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/angler-opm7.181205.001-factory-b75ce068.zip" class="gc-analytics-event" data-category="Android Images" data-label="angler for Nexus 6P [OPM7.181205.001]">Link</a></td>
    <td>b75ce068f23a0e793805f80fccbc081eca52861ef5eb080c47f502de4c3f9713</td>
  </tr>
</tbody></table></div>

<h2 id="bullhead" is-upgraded="">"bullhead" for Nexus 5X</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="bullheadmda89e">
    <td>6.0.0 (MDA89E)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mda89e-factory-d716b566.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MDA89E]">Link</a></td>
    <td>d716b566f82f8716287592febeee294792dfd32edbe9cdd6e9f5ced38b54cadc</td>
  </tr>
  <tr id="bullheadmdb08i">
    <td>6.0.0 (MDB08I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mdb08i-factory-329f6582.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MDB08I]">Link</a></td>
    <td>329f65828483310fffcd4615ec15583f41f63a4442c880efc4e81154c4f6040e</td>
  </tr>
  <tr id="bullheadmdb08l">
    <td>6.0.0 (MDB08L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mdb08l-factory-69995ae9.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MDB08L]">Link</a></td>
    <td>69995ae939970e1fe9e954ad8ecaf046aab046ac133bdcd0eb5e162ddc56d53d</td>
  </tr>
  <tr id="bullheadmdb08m">
    <td>6.0.0 (MDB08M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mdb08m-factory-9f8fb666.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MDB08M]">Link</a></td>
    <td>9f8fb666e998999fb8317c21fea9a34082c32ff26322a51994b506aec54388de</td>
  </tr>
  <tr id="bullheadmmb29k">
    <td>6.0.1 (MMB29K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mmb29k-factory-c3b91ce3.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MMB29K]">Link</a></td>
    <td>c3b91ce36655f47a63d26b6c6b94278e278049785de0de1df1bb1a1a8a9f4247</td>
  </tr>
  <tr id="bullheadmmb29p">
    <td>6.0.1 (MMB29P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mmb29p-factory-806ea72b.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MMB29P]">Link</a></td>
    <td>806ea72b44b60dd62e4ac621244fc9d9e6d8f6930209f78456ffb448441b7036</td>
  </tr>
  <tr id="bullheadmmb29q">
    <td>6.0.1 (MMB29Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mmb29q-factory-f8228950.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MMB29Q]">Link</a></td>
    <td>f82289500de3ac128452e0a91e98c42e940771bbe4c243827ad419dc73d42c31</td>
  </tr>
  <tr id="bullheadmmb29v">
    <td>6.0.1 (MMB29V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mmb29v-factory-09b6d3d2.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MMB29V]">Link</a></td>
    <td>09b6d3d2770f75f82451a8ea03d5121e41dc070b1f286c785f17864a76ae480d</td>
  </tr>
  <tr id="bullheadmhc19j">
    <td>6.0.1 (MHC19J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mhc19j-factory-8083681d.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MHC19J]">Link</a></td>
    <td>8083681de1a1e0686788d7ebeb4215a01aaa994e238dc3ffab4c4bd73d674389</td>
  </tr>
  <tr id="bullheadmhc19q">
    <td>6.0.1 (MHC19Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mhc19q-factory-2e43836c.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MHC19Q]">Link</a></td>
    <td>2e43836c99d6c78ce45b62a4591a151094ff4eb88aa08672ad4c9c1d63c9c9bb</td>
  </tr>
  <tr id="bullheadmtc19t">
    <td>6.0.1 (MTC19T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mtc19t-factory-dea1dfba.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MTC19T]">Link</a></td>
    <td>dea1dfba857970acf3cb0aef10b826d2d40ed5467f478293bcd1e4a8f9821850</td>
  </tr>
  <tr id="bullheadmtc19v">
    <td>6.0.1 (MTC19V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mtc19v-factory-61de3a6f.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MTC19V]">Link</a></td>
    <td>61de3a6fa4ef9284972adae7deeec58a3e92528d6aa7637d31539f37deff345e</td>
  </tr>
  <tr id="bullheadmtc19z">
    <td>6.0.1 (MTC19Z)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mtc19z-factory-953a60d3.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MTC19Z]">Link</a></td>
    <td>953a60d30ac717cdd5228492afffe108199ca4244e5bd3b68caa6d3d47449395</td>
  </tr>
  <tr id="bullheadmtc20f">
    <td>6.0.1 (MTC20F)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mtc20f-factory-fa466167.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MTC20F]">Link</a></td>
    <td>fa4661677b9c973a4d0a4ee50fed241af618904cd39c10d8682712fcfd327035</td>
  </tr>
  <tr id="bullheadmtc20k">
    <td>6.0.1 (MTC20K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-mtc20k-factory-4a950470.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [MTC20K]">Link</a></td>
    <td>4a950470af6c1e0111cfa8efbd77422928b88d01800dd2fadc6f8eeeae1b97a9</td>
  </tr>
  <tr id="bullheadnrd90m">
    <td>7.0.0 (NRD90M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-nrd90m-factory-61495c8b.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [NRD90M]">Link</a></td>
    <td>61495c8b4e22e8ddb1522278905db3e571bb707d9ccddae8b0bdeab670fa8453</td>
  </tr>
  <tr id="bullheadnrd90r">
    <td>7.0.0 (NRD90R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-nrd90r-factory-dc60b38f.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [NRD90R]">Link</a></td>
    <td>dc60b38f8f248aff594e4fce28d59727b0f2448817bd382eb1a86adb096b31ca</td>
  </tr>
  <tr id="bullheadnrd90s">
    <td>7.0.0 (NRD90S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-nrd90s-factory-d6bf1f56.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [NRD90S]">Link</a></td>
    <td>d6bf1f56311f03903908a7fa20f75e5f9c2d21d5cbe4cc26aeb85b19a05544df</td>
  </tr>
  <tr id="bullheadnbd90w">
    <td>7.0.0 (NBD90W, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-nbd90w-factory-d2f11c5f.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [NBD90W]">Link</a></td>
    <td>d2f11c5f22d71eff939996291cb7430be2b9c29e8078765a10c935c29d7e5c38</td>
  </tr>
  <tr id="bullheadnrd91n">
    <td>7.0.0 (NRD91N, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-nrd91n-factory-7a2e3942.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [NRD91N]">Link</a></td>
    <td>7a2e3942c5963e51ce31ad5cedcb0a634d3c258c85188e4c273c903fa1cece14</td>
  </tr>
  <tr id="bullheadn5d91l">
    <td>7.0.0 (N5D91L, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n5d91l-factory-7151a923.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N5D91L]">Link</a></td>
    <td>7151a9237e64b64f53e50684bc1e0cef5143a40aebf74d4906425edf06f2ed89</td>
  </tr>
  <tr id="bullheadnmf26f">
    <td>7.1.1 (NMF26F, Dec 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-nmf26f-factory-7ad6b52c.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [NMF26F]">Link</a></td>
    <td>7ad6b52c7f1aba6021dd256c3c4746299ecda3ccd39e7694a815e182daccbe16</td>
  </tr>
  <tr id="bullheadn4f26i">
    <td>7.1.1 (N4F26I, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n4f26i-factory-03896e0a.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N4F26I]">Link</a></td>
    <td>03896e0adb2ed6b19f0e3b8554763e48a16d9239449724c9a483cb69f6db93f7</td>
  </tr>
  <tr id="bullheadn4f26o">
    <td>7.1.1 (N4F26O, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n4f26o-factory-1da5304e.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N4F26O]">Link</a></td>
    <td>1da5304e52c43ae0fad1828fce9b60656b3c0613120a43f97d1101e857fdef75</td>
  </tr>
  <tr id="bullheadn4f26t">
    <td>7.1.1 (N4F26T, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n4f26t-factory-8eed1d9f.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N4F26T]">Link</a></td>
    <td>8eed1d9fc7f3d6365cdd41d10f0adab3888f97eeae6631f4afde9239ff0e585d</td>
  </tr>
  <tr id="bullheadn4f26u">
    <td>7.1.1 (N4F26U, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n4f26u-factory-e6420fc1.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N4F26U]">Link</a></td>
    <td>e6420fc10c3bce4625c75b2b322ccfdb6526259d9aebad32ba75af2e2114354e</td>
  </tr>
  <tr id="bullheadn2g47f">
    <td>7.1.2 (N2G47F, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n2g47f-factory-f5d53a67.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N2G47F]">Link</a></td>
    <td>f5d53a67662d1b4c2b2325813d823fc49ad9fb4a5b5361e91c3aff00157c1ddf</td>
  </tr>
  <tr id="bullheadn2g47o">
    <td>7.1.2 (N2G47O, May 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n2g47o-factory-3ff32f55.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N2G47O]">Link</a></td>
    <td>3ff32f55daae9d973021c3e67480d3210ace7aabc48eede762d2cea29180e3b2</td>
  </tr>
  <tr id="bullheadn2g47w">
    <td>7.1.2 (N2G47W, Jun 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n2g47w-factory-e4179e51.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N2G47W]">Link</a></td>
    <td>e4179e510e8fb930c42676d1fcfebeea4e3dfa648287834552e89c7bfc05132f</td>
  </tr>
  <tr id="bullheadn2g47z">
    <td>7.1.2 (N2G47Z, Jul 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n2g47z-factory-c3573ae2.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N2G47Z]">Link</a></td>
    <td>c3573ae2252cdc98d7f6e2d3ef31f79b97e38a44977e6d252158bfeaa152114c</td>
  </tr>
  <tr id="bullheadn2g48c">
    <td>7.1.2 (N2G48C, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-n2g48c-factory-45d442a2.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [N2G48C]">Link</a></td>
    <td>45d442a26832292df258d7be83de160f280681fa57a12932a3bccfbf088fc337</td>
  </tr>
  <tr id="bullheadopr6.170623.013">
    <td>8.0.0 (OPR6.170623.013, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opr6.170623.013-factory-203642e1.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPR6.170623.013]">Link</a></td>
    <td>203642e1a27ee0f00302cbf0003adfb8fabfb27821a6f33bad393472a20b97c8</td>
  </tr>
  <tr id="bullheadopr4.170623.006">
    <td>8.0.0 (OPR4.170623.006, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opr4.170623.006-factory-e876a276.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPR4.170623.006]">Link</a></td>
    <td>e876a2762a721ba12abbe6849d31b4aa2c5eeff8decdc558d9964a1ee0403936</td>
  </tr>
  <tr id="bullheadopr4.170623.009">
    <td>8.0.0 (OPR4.170623.009, Oct 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opr4.170623.009-factory-b9f20abf.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPR4.170623.009]">Link</a></td>
    <td>b9f20abf22bb2eb912ad66db316eb83f775871d7d953450294df33bd8a91baf2</td>
  </tr>
  <tr id="bullheadopr6.170623.023">
    <td>8.0.0 (OPR6.170623.023, Nov 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opr6.170623.023-factory-71c4191e.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPR6.170623.023]">Link</a></td>
    <td>71c4191efdfa2b9a293c0f59fa6865d99caadc4d99881f4b09b37c61cace4efd</td>
  </tr>
  <tr id="bullheadopr4.170623.020">
    <td>8.0.0 (OPR4.170623.020, Dec 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opr4.170623.020-factory-152b858b.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPR4.170623.020]">Link</a></td>
    <td>152b858b7b89649327db77b8fabca8afc65b5f898eb7c5ffaa0c3b2321c17002</td>
  </tr>
  <tr id="bullheadopm1.171019.011">
    <td>8.1.0 (OPM1.171019.011, Dec 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm1.171019.011-factory-3be6fd1c.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM1.171019.011]">Link</a></td>
    <td>3be6fd1c8ad9759f1f77f0f2e62fae62ffdbe98d1b8f49af39e2ec7024ae7804</td>
  </tr>
  <tr id="bullheadopm3.171019.013">
    <td>8.1.0 (OPM3.171019.013, Jan 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm3.171019.013-factory-20d65754.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM3.171019.013]">Link</a></td>
    <td>20d6575420a4e5861903ac1941c454410f306b0ba2522353e7240ade8a536c5b</td>
  </tr>
  <tr id="bullheadopm5.171019.014">
    <td>8.1.0 (OPM5.171019.014, Jan 2018, Telstra and Softbank)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm5.171019.014-factory-2f815bac.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM5.171019.014]">Link</a></td>
    <td>2f815bacf3c2a0b839895a1903242afbf461dc84ad62e0f4483f1c75c5fdd697</td>
  </tr>
  <tr id="bullheadopm3.171019.014">
    <td>8.1.0 (OPM3.171019.014, Feb 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm3.171019.014-factory-79f53247.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM3.171019.014]">Link</a></td>
    <td>79f532473db66f4a494229198d967601e104a4a2f7acbfa246ce512c43926f29</td>
  </tr>
  <tr id="bullheadopm5.171019.015">
    <td>8.1.0 (OPM5.171019.015, Feb 2018, Telstra and Softbank)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm5.171019.015-factory-1a2de10b.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM5.171019.015]">Link</a></td>
    <td>1a2de10b9f7aadfdad29244b2627b62eadcc208a52b64205146f82e8d29d1b8c</td>
  </tr>
  <tr id="bullheadopm3.171019.016">
    <td>8.1.0 (OPM3.171019.016, Mar 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm3.171019.016-factory-6e4c89cb.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM3.171019.016]">Link</a></td>
    <td>6e4c89cba89bc9135abf3e8c12fcbf2c2fe77ceaf6ec6dbbb532baa78acf2f50</td>
  </tr>
  <tr id="bullheadopm5.171019.017">
    <td>8.1.0 (OPM5.171019.017, Mar 2018, Telstra and Softbank)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm5.171019.017-factory-5c65d443.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM5.171019.017]">Link</a></td>
    <td>5c65d4433dea790953c542fa8b7a44f949e35c568e55f06d2ad1726b42bbf1d3</td>
  </tr>
  <tr id="bullheadopm2.171019.029">
    <td>8.1.0 (OPM2.171019.029, Apr 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm2.171019.029-factory-c7ba966b.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM2.171019.029]">Link</a></td>
    <td>c7ba966bb89462517e7c425773bc30fa26aff73f3a2ac350ea5617186f574b7e</td>
  </tr>
  <tr id="bullheadopm4.171019.016.a1">
    <td>8.1.0 (OPM4.171019.016.A1, May 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm4.171019.016.a1-factory-d5756448.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM4.171019.016.A1]">Link</a></td>
    <td>d5756448fee7fefc556c9c804bee4fa02cfe2e95eb12ba9afd4f504e67e83413</td>
  </tr>
  <tr id="bullheadopm6.171019.030.b1">
    <td>8.1.0 (OPM6.171019.030.B1, Jun 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm6.171019.030.b1-factory-b3487a6c.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM6.171019.030.B1]">Link</a></td>
    <td>b3487a6c5eccdb8bdfed9f2be4d58ca89ec3ec431cf6c5e67cfdd494a2c3e8e4</td>
  </tr>
  <tr id="bullheadopm6.171019.030.e1">
    <td>8.1.0 (OPM6.171019.030.E1, Jul 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm6.171019.030.e1-factory-0650f4c3.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM6.171019.030.E1]">Link</a></td>
    <td>0650f4c3118bc49f58fe7bbacb37aeed589702dd1ca6b11e69c413fdca3a14f5</td>
  </tr>
  <tr id="bullheadopm6.171019.030.h1">
    <td>8.1.0 (OPM6.171019.030.H1, Aug 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm6.171019.030.h1-factory-81957f7f.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM6.171019.030.H1]">Link</a></td>
    <td>81957f7fcbf6d47a595e9369dbbcc856d9918f6ee085882cc71376bc7c27e724</td>
  </tr>
  <tr id="bullheadopm6.171019.030.k1">
    <td>8.1.0 (OPM6.171019.030.K1, Sep 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm6.171019.030.k1-factory-0ae3cd15.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM6.171019.030.K1]">Link</a></td>
    <td>0ae3cd15376f946ad25695d75857a32c69bed28fbc6642a743057331fa5f4b22</td>
  </tr>
  <tr id="bullheadopm7.181005.003">
    <td>8.1.0 (OPM7.181005.003, Oct 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm7.181005.003-factory-e23fac1c.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM7.181005.003]">Link</a></td>
    <td>e23fac1c7995e47e12823e3db577bb16f19894cb80545d3103e0087a396a1d2f</td>
  </tr>
  <tr id="bullheadopm7.181105.004">
    <td>8.1.0 (OPM7.181105.004, Nov 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm7.181105.004-factory-37df0288.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM7.181105.004]">Link</a></td>
    <td>37df02882d3c90cebabf21fccc8f19094741f0694efd63f5c4f8787aecc9d8d2</td>
  </tr>
  <tr id="bullheadopm7.181205.001">
    <td>8.1.0 (OPM7.181205.001, Dec 2018)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/bullhead-opm7.181205.001-factory-5f189d84.zip" class="gc-analytics-event" data-category="Android Images" data-label="bullhead for Nexus 5X [OPM7.181205.001]">Link</a></td>
    <td>5f189d84781a26b49aca0de84a941a32ae0150da0aab89f1d7709d56c31b3c0a</td>
  </tr>
</tbody></table></div>

<h2 id="shamu" is-upgraded="">"shamu" for Nexus 6</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="shamulrx21o">
    <td>5.0 (LRX21O)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lrx21o-factory-ef423ec5.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LRX21O]">Link</a></td>
    <td>ef423ec5ab0f3f2370681206236b9e1817a7512375ce189352bc52a8a39d0a55</td>
  </tr>
  <tr id="shamulrx22c">
    <td>5.0.1 (LRX22C)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lrx22c-factory-2b930c37.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LRX22C]">Link</a></td>
    <td>2b930c37ced6aee159f7c2bfa1609f61976057339b2a7fb05636267f95a687c1</td>
  </tr>
  <tr id="shamulmy47d">
    <td>5.1.0 (LMY47D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy47d-factory-228e9d64.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY47D]">Link</a></td>
    <td>228e9d64b34063d430700316b13a494277b12e519d7a74f2e51d71645b3f69a2</td>
  </tr>
  <tr id="shamulmy47e">
    <td>5.1.0 (LMY47E)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy47e-factory-9aeac3ca.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY47E]">Link</a></td>
    <td>9aeac3ca510f5aad8263e5656a10f0fef3a78a743253013b2803c2e6817cced1</td>
  </tr>
  <tr id="shamulmy47i">
    <td>5.1.0 (LMY47I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy47i-factory-3a0545d8.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY47I]">Link</a></td>
    <td>3a0545d80e2e1099069b952abb03fead6481d7d4a6eacf73559bb1f96278f308</td>
  </tr>
  <tr id="shamulmy47m">
    <td>5.1.0 (For T-Mobile ONLY) (LMY47M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy47m-factory-617139c6.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY47M]">Link</a></td>
    <td>617139c68a41784e5e971a0ff25212605bc8ced67df0c690c3b6667aa80e5284</td>
  </tr>
  <tr id="shamulmy47z">
    <td>5.1.1 (All carriers except T-Mobile US) (LMY47Z)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy47z-factory-81b798d6.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY47Z]">Link</a></td>
    <td>81b798d603186730e99c701053402156cb43b96a4f0f87daa22d78df2116a519</td>
  </tr>
  <tr id="shamulyz28e">
    <td>5.1.1 (For T-Mobile ONLY) (LYZ28E)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lyz28e-factory-d8d3c84e.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LYZ28E]">Link</a></td>
    <td>d8d3c84eb70b4c593a1b30a4ec228d6c6072f5f11f2d037c153f95cd7567825f</td>
  </tr>
  <tr id="shamulvy48c">
    <td>5.1.1 (For Project Fi ONLY) (LVY48C)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lvy48c-factory-a1cf7213.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LVY48C]">Link</a></td>
    <td>a1cf7213cfac6213b8c18c49ec0476d92b70286a0346eb8588d46a164dde3577</td>
  </tr>
  <tr id="shamulmy48i">
    <td>5.1.1 (LMY48I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy48i-factory-70635eea.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY48I]">Link</a></td>
    <td>70635eeaab9de2a2bca1cc5b0fdf84917ce07d13dcfcbf422052f16ccf663a92</td>
  </tr>
  <tr id="shamulyz28j">
    <td>5.1.1 (For T-Mobile ONLY) (LYZ28J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lyz28j-factory-0296e96f.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LYZ28J]">Link</a></td>
    <td>0296e96f8a23b6c4562a8535e9c2af9955edef09d09c98c8947d7ff6610c800e</td>
  </tr>
  <tr id="shamulvy48e">
    <td>5.1.1 (For Project Fi ONLY) (LVY48E)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lvy48e-factory-bb92198f.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LVY48E]">Link</a></td>
    <td>bb92198f1c3b37da8c6933421bd898f282ec28b4661d5c1a9151b247b4af78ed</td>
  </tr>
  <tr id="shamulmy48m">
    <td>5.1.1 (LMY48M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy48m-factory-25210911.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY48M]">Link</a></td>
    <td>25210911286e7959c4237fbeeb12db0214b094f94aba90b18365c23cd825cabe</td>
  </tr>
  <tr id="shamulyz28k">
    <td>5.1.1 (For T-Mobile ONLY) (LYZ28K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lyz28k-factory-306b611d.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LYZ28K]">Link</a></td>
    <td>306b611df1796fa5795925f70066218ba75585825e0ae8241ed95b4a2959ee97</td>
  </tr>
  <tr id="shamulvy48f">
    <td>5.1.1 (For Project Fi ONLY) (LVY48F)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lvy48f-factory-caf25cb7.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LVY48F]">Link</a></td>
    <td>caf25cb7400b9cc3177c5f8d0e9d550cf39fc5c6e2f7d024f26d1b49f2e644f5</td>
  </tr>
  <tr id="shamulmy48t">
    <td>5.1.1 (LMY48T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy48t-factory-afc4b8b7.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY48T]">Link</a></td>
    <td>afc4b8b70c2c4ee68a287ed64bd1e435b9731083faee677981ad314146d1d93b</td>
  </tr>
  <tr id="shamulyz28m">
    <td>5.1.1 (For T-Mobile ONLY) (LYZ28M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lyz28m-factory-dd3dcb20.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LYZ28M]">Link</a></td>
    <td>dd3dcb2028c57638b1c837951dc6ca56873ec44aef7bbc876c55602151e858d1</td>
  </tr>
  <tr id="shamulvy48h">
    <td>5.1.1 (For Project Fi ONLY) (LVY48H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lvy48h-factory-d197efba.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LVY48H]">Link</a></td>
    <td>d197efba5e74588d35c77db8905423a71be8311c2a1058a3c7871ccc4ebedd71</td>
  </tr>
  <tr id="shamulmy48w">
    <td>5.1.1 (LMY48W)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy48w-factory-403fe322.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY48W]">Link</a></td>
    <td>403fe3222fe103fae11ffd7ee27486aacc6479c69c9760e03cc4c430e1014a28</td>
  </tr>
  <tr id="shamulmy48x">
    <td>5.1.1 (LMY48X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy48x-factory-2bf8d6fd.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY48X]">Link</a></td>
    <td>2bf8d6fde027e0161d2eb3c45ea997016fdd8cc879f7201bd469d757209922c7</td>
  </tr>
  <tr id="shamulmy48y">
    <td>5.1.1 (LMY48Y)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lmy48y-factory-505ed306.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LMY48Y]">Link</a></td>
    <td>505ed3067bb04e45374eaad707e729c08b5d06586016c9c218449091f879732a</td>
  </tr>
  <tr id="shamulyz28n">
    <td>5.1.1 (For T-Mobile ONLY) (LYZ28N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lyz28n-factory-5dffe2dc.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LYZ28N]">Link</a></td>
    <td>5dffe2dccf71c1859a2c58d80a08e372cea3b8d49c20dbbcce5f520d1522e860</td>
  </tr>
  <tr id="shamulvy48i">
    <td>5.1.1 (For Project Fi ONLY) (LVY48I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-lvy48i-factory-e9cedcb8.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [LVY48I]">Link</a></td>
    <td>e9cedcb8f4f0be18576b7317fe915bbf868907be9859a2201b536d182f171789</td>
  </tr>
  <tr id="shamumra58k">
    <td>6.0.0 (MRA58K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mra58k-factory-0c8cee76.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MRA58K]">Link</a></td>
    <td>0c8cee76432db6fc40c169a61bbd6286b76e06bc5ebf5c79b2feba1b87e46660</td>
  </tr>
  <tr id="shamumra58n">
    <td>6.0.0 (MRA58N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mra58n-factory-330ade99.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MRA58N]">Link</a></td>
    <td>330ade99ba383bb263d8ec2bbfc8e936053d29080dc3c854cf0d2ec9a83d79fc</td>
  </tr>
  <tr id="shamumra58r">
    <td>6.0.0 (MRA58R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mra58r-factory-0c3e2d0b.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MRA58R]">Link</a></td>
    <td>0c3e2d0b5a4af48eb665836bb64c6a4c95554ba6efe9a3fad9cdc226afa1b65a</td>
  </tr>
  <tr id="shamumra58x">
    <td>6.0.0 (MRA58X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mra58x-factory-9a184014.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MRA58X]">Link</a></td>
    <td>9a18401432138127943e8ac2464d4f7b80920f8e6d74855a7adf8a037a4ae42a</td>
  </tr>
  <tr id="shamummb29k">
    <td>6.0.1 (MMB29K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb29k-factory-374c4c6a.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB29K]">Link</a></td>
    <td>374c4c6adfc65c5c4202bde51647c1a949ef26fdd7820668eb9e509fa410ba80</td>
  </tr>
  <tr id="shamummb29s">
    <td>6.0.1 (MMB29S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb29s-factory-a593f97c.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB29S]">Link</a></td>
    <td>a593f97c033cf678dd282c5216fcf920c1cea1e9ff6ae02fb44cfe8c21b618ca</td>
  </tr>
  <tr id="shamummb29q">
    <td>6.0.1 (MMB29Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb29q-factory-b6c05f68.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB29Q]">Link</a></td>
    <td>b6c05f68f0613d117f589f03325c4dd4bc025188e41df715e3a7696f803d4ea4</td>
  </tr>
  <tr id="shamummb29v">
    <td>6.0.1 (MMB29V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb29v-factory-eb823e76.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB29V]">Link</a></td>
    <td>eb823e767cdd926638a00cf410a0580915c2a3e9d954c7dcffcf6835ee8b777a</td>
  </tr>
  <tr id="shamummb29x">
    <td>6.0.1 (MMB29X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb29x-factory-64449878.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB29X]">Link</a></td>
    <td>64449878d12147532f8664a3f2bf47801698e4f791ab807f2fe99549898e4080</td>
  </tr>
  <tr id="shamumob30d">
    <td>6.0.1 (MOB30D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob30d-factory-df7014f9.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MOB30D]">Link</a></td>
    <td>df7014f9417a886bc9efc79d9a3548add5e0a18aea47f73ad3cd9e535e450db0</td>
  </tr>
  <tr id="shamummb30g">
    <td>6.0.1 (MMB30G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb30g-factory-d5d540ed.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB30G]">Link</a></td>
    <td>d5d540ed1bd8f8a544740dd75f2e8e61a43a15c13a9fa2e4312e86e59830ea36</td>
  </tr>
  <tr id="shamumob30i">
    <td>6.0.1 (MOB30I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob30i-factory-3692dac3.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MOB30I]">Link</a></td>
    <td>3692dac3560b0e03b5bab4c113ea9ebe1def8c4cbc54260b5cf5027829332a1e</td>
  </tr>
  <tr id="shamummb30j">
    <td>6.0.1 (MMB30J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb30j-factory-dc940f6b.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB30J]">Link</a></td>
    <td>dc940f6b6baeadf295806456c46fb1ca4800f1bdb43b3f92c257271ef419b8e1</td>
  </tr>
  <tr id="shamumob30m">
    <td>6.0.1 (MOB30M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob30m-factory-e0a74382.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MOB30M]">Link</a></td>
    <td>e0a743824b3abf397d0d7158779356dc9bb5d9d6d34c1396209a379e06fee9ea</td>
  </tr>
  <tr id="shamummb30k">
    <td>6.0.1 (MMB30K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb30k-factory-3db93497.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB30K]">Link</a></td>
    <td>3db934979cafe6c35448e8cff0c035e1e82b198e8577206e60a6a5da8b369961</td>
  </tr>
  <tr id="shamumob30o">
    <td>6.0.1 (MOB30O)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob30o-factory-5d20bd38.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MOB30O]">Link</a></td>
    <td>5d20bd38d77b33ae38c54fefe6fcef60a99270a13bdb5f780a2191b477950cf6</td>
  </tr>
  <tr id="shamummb30r">
    <td>6.0.1 (MMB30R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb30r-factory-d5878426.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB30R]">Link</a></td>
    <td>d587842660034fd6dc72b85c09b419ee96f68102ab35f7e6b6bbdbaeaaba7071</td>
  </tr>
  <tr id="shamumob30w">
    <td>6.0.1 (MOB30W)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob30w-factory-21715256.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MOB30W]">Link</a></td>
    <td>21715256ba8d5e745954239b8da810e75f32e9ffed9bcd99bdd41e2a39d31647</td>
  </tr>
  <tr id="shamummb30w">
    <td>6.0.1 (MMB30W)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb30w-factory-9a710d33.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB30W]">Link</a></td>
    <td>9a710d332de151cbdadaef3cfbb18641802d4f37c5ce5a4e2f5345799e9cf23d</td>
  </tr>
  <tr id="shamumob31e">
    <td>6.0.1 (MOB31E)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob31e-factory-051e2d25.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MOB31E]">Link</a></td>
    <td>051e2d2525fcfc422c73e95bf360437c241789ea65a42bd95800f84f9da7a7e8</td>
  </tr>
  <tr id="shamummb30y">
    <td>6.0.1 (MMB30Y, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb30y-factory-95eac974.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MMB30Y]">Link</a></td>
    <td>95eac974e01661d62fd115180b028116597f08c9b90eae0395719870b74d182d</td>
  </tr>
  <tr id="shamumob31h">
    <td>6.0.1 (MOB31H, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob31h-factory-5ef08d52.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [MOB31H]">Link</a></td>
    <td>5ef08d521a7bd1df742bd81363ba0f59ed489983e48fc87769ae039080c4edc5</td>
  </tr>
  <tr id="shamunbd90z">
    <td>7.0.0 (NBD90Z, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd90z-factory-92e7bb05.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 [NBD90Z]">Link</a></td>
    <td>92e7bb058e3842fab33241feb2d315cb3ff9c00d9a8bb75d3fee4a70cfe9e841</td>
  </tr>
  <tr id="shamummb31c">
    <td>6.0.1 (MMB31C, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mmb31c-factory-dd075f34.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [MMB31C]">Link</a></td>
    <td>dd075f342df42597aefb588d4cc851cdfe22efbada1039db4e217e9232af1f6d</td>
  </tr>
  <tr id="shamumob31k">
    <td>6.0.1 (MOB31K, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob31k-factory-49a4de6b.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [MOB31K]">Link</a></td>
    <td>49a4de6b7ac963184da86e071002ccfb303b5afecf1a9b6fae77f5f6285c0a03</td>
  </tr>
  <tr id="shamunbd91p">
    <td>7.0.0 (NBD91P, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd91p-factory-987282ff.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NBD91P]">Link</a></td>
    <td>987282ffca6918cf82585b040d6e3dccf4895b9241a23d807925c56adbb179a3</td>
  </tr>
  <tr id="shamunbd91u">
    <td>7.0.0 (NBD91U, Dec 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd91u-factory-1aca1562.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NBD91U]">Link</a></td>
    <td>1aca15622a90922a37a8b0071c60edabe241e72303c23219ce9d4f1e5a67f6a1</td>
  </tr>
  <tr id="shamumob31s">
    <td>6.0.1 (MOB31S, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob31s-factory-c73a35ef.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [MOB31S]">Link</a></td>
    <td>c73a35efb3e089177f94f758de9dff8fde0df77c27bb26be4cc876ee47d0d171</td>
  </tr>
  <tr id="shamunbd91x">
    <td>7.0.0 (NBD91X, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd91x-factory-f653ffea.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NBD91X]">Link</a></td>
    <td>f653ffeabf1a2ef0d1c8b7b9cf85511198fcf5a2961982dc030d8f82b3830540</td>
  </tr>
  <tr id="shamun6f26q">
    <td>7.1.1 (N6F26Q, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n6f26q-factory-460b565b.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N6F26Q]">Link</a></td>
    <td>460b565b5939e29cd74811392f12690a0bb9fc8ced172df13935248e3f9f657b</td>
  </tr>
  <tr id="shamumob31t">
    <td>6.0.1 (MOB31T, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-mob31t-factory-a40106ff.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [MOB31T]">Link</a></td>
    <td>a40106ffa0d636c705e3fd045e3cf97b8217aae3fae67038fec675a5a9a799fc</td>
  </tr>
  <tr id="shamunbd91y">
    <td>7.0.0 (NBD91Y, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd91y-factory-7e2f4915.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NBD91Y]">Link</a></td>
    <td>7e2f49150a570961f6e0a28083d9f932b2ff401af983c6b02e898bcd9bd4be18</td>
  </tr>
  <tr id="shamunbd91z">
    <td>7.0.0 (NBD91Z, Feb 2017, ATT Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd91z-factory-ffb1f6a6.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NBD91Z]">Link</a></td>
    <td>ffb1f6a6beb63fb932c86cc329c59038f4e49254316dcf2d825376e77beb5a48</td>
  </tr>
  <tr id="shamun6f26r">
    <td>7.1.1 (N6F26R, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n6f26r-factory-d68bd4ce.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N6F26R]">Link</a></td>
    <td>d68bd4ce70cd7d94a098d16e949c6677264cb699d36e8ee29acb7162103dfeee</td>
  </tr>
  <tr id="shamunbd92d">
    <td>7.0.0 (NBD92D, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd92d-factory-a5e9a1f5.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NBD92D]">Link</a></td>
    <td>a5e9a1f535d69769caa72015d7dffc17e0a35e736f127b956f042abdaf1adbc9</td>
  </tr>
  <tr id="shamunbd92e">
    <td>7.0.0 (NBD92E, Mar 2017, ATT Only)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd92e-factory-1ad7d1a4.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NBD92E]">Link</a></td>
    <td>1ad7d1a49d15b7eccb0c41a7653a0eae5f147f64debd5bfe1d035aa00d51eae3</td>
  </tr>
  <tr id="shamun6f26u">
    <td>7.1.1 (N6F26U, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n6f26u-factory-6e52aa95.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N6F26U]">Link</a></td>
    <td>6e52aa95b48d4d8e1f191e4370e4207b92b822100846d0cd6b8bf6ce2ebfa0f2</td>
  </tr>
  <tr id="shamunbd92f">
    <td>7.0.0 (NBD92F, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd92f-factory-55370c9d.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NBD92F]">Link</a></td>
    <td>55370c9de0c7b5edb8dfde126148eff68a88ceee224fb103c76867055b0b9dfc</td>
  </tr>
  <tr id="shamunbd92g">
    <td>7.0.0 (NBD92G, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-nbd92g-factory-28a47aa1.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NBD92G]">Link</a></td>
    <td>28a47aa1bf6909ccd04bdcef375d1af64abb898b1d31e3bbf9c8b58e0837d85b</td>
  </tr>
  <tr id="shamun6f26y">
    <td>7.1.1 (N6F26Y, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n6f26y-factory-fdd4bbc7.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N6F26Y]">Link</a></td>
    <td>fdd4bbc7bf72e612973231bfb46bf0df14a39304ba7de788fbf4dd10e281c387</td>
  </tr>
  <tr id="shamun6f27c">
    <td>7.1.1 (N6F27C, May 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n6f27c-factory-5a3649b7.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N6F27C]">Link</a></td>
    <td>5a3649b7049e74196a449eb4c28296064c565aba72049727476d9377db0e9f7c</td>
  </tr>
  <tr id="shamun6f27e">
    <td>7.1.1 (N6F27E, Jun 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n6f27e-factory-74a9a99e.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N6F27E]">Link</a></td>
    <td>74a9a99ec3532ee39e5c5bde92e659d3b2b3884245f852998c2f9425c842d177</td>
  </tr>
  <tr id="shamun6f27h">
    <td>7.1.1 (N6F27H, Jul 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n6f27h-factory-718e138f.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N6F27H]">Link</a></td>
    <td>718e138faec60f7c065dd738011a720e9e3ff76101f7b9c614a756f487947197</td>
  </tr>
  <tr id="shamun6f27i">
    <td>7.1.1 (N6F27I, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n6f27i-factory-edc6a1ba.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N6F27I]">Link</a></td>
    <td>edc6a1ba19d1fabfdeb1d2fdf6c2725e3be40c0eb8823f187449f710c86a64cd</td>
  </tr>
  <tr id="shamun8i11b">
    <td>7.1.1 (N8I11B, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n8i11b-factory-9f65ba63.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N8I11B]">Link</a></td>
    <td>9f65ba637a135f7ed050c9d2e26bb47c23b0b79ca18711285e3853e4a54490d2</td>
  </tr>
  <tr id="shamungi55d">
    <td>7.1.1 (NGI55D, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-ngi55d-factory-1132151d.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NGI55D]">Link</a></td>
    <td>1132151de197efe0bd8903aeccf7b097c0d3d52a07238e355eb7be35206e6737</td>
  </tr>
  <tr id="shamun6f27m">
    <td>7.1.1 (N6F27M, Oct 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n6f27m-factory-bf5cce08.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N6F27M]">Link</a></td>
    <td>bf5cce08f62344d79d5b533875c3485a03accf45bd28f45a4455154a2d83618c</td>
  </tr>
  <tr id="shamun8i11f">
    <td>7.1.1 (N8I11F, Oct 2017, T-Mobile)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-n8i11f-factory-ae7e8dcf.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [N8I11F]">Link</a></td>
    <td>ae7e8dcf559a9efc155eac9900cd4b07174ab916d4a95b350a09e1d35ed7a4b0</td>
  </tr>
  <tr id="shamungi77b">
    <td>7.1.1 (NGI77B, Oct 2017, Verizon)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/shamu-ngi77b-factory-5cd75e2a.zip" class="gc-analytics-event" data-category="Android Images" data-label="shamu for Nexus 6 (Mobile) [NGI77B]">Link</a></td>
    <td>5cd75e2a3bbbe5d7cf886f6dba4dbfc16a04076e6ace11b4deeb1dc4e43b7465</td>
  </tr>
</tbody></table></div>

<h2 id="fugu" is-upgraded="">"fugu" for Nexus Player</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="fugulrx21m">
    <td>5.0 (LRX21M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-lrx21m-factory-e012394c.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [LRX21M]">Link</a></td>
    <td>e012394cf4ee5cd2c8957f616a23a6f5f87cb04563265fef49507d5ec3b24032</td>
  </tr>
  <tr id="fugulrx21v">
    <td>5.0 (LRX21V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-lrx21v-factory-2f283d96.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [LRX21V]">Link</a></td>
    <td>2f283d965537cbb19c7b694692cea2b1c9adcd64beb2070bec0f745c62f527d2</td>
  </tr>
  <tr id="fugulmy47d">
    <td>5.1.0 (LMY47D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-lmy47d-factory-3704b408.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [LMY47D]">Link</a></td>
    <td>3704b4084f2e6716ba7fa220732006bc78d5435628ae9fd9d371077f2dbbd6e2</td>
  </tr>
  <tr id="fugulmy47v">
    <td>5.1.1 (LMY47V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-lmy47v-factory-c9a59be3.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [LMY47V]">Link</a></td>
    <td>c9a59be3af6db26cb76b5f492d900dfa1a424f2403733b98c300d39183dabfd3</td>
  </tr>
  <tr id="fugulmy48j">
    <td>5.1.1 (LMY48J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-lmy48j-factory-c7b4e4c0.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [LMY48J]">Link</a></td>
    <td>c7b4e4c0afe8307ec8500249c237667afb7b46b27fdd0511571f8ffba97139f3</td>
  </tr>
  <tr id="fugulmy48n">
    <td>5.1.1 (LMY48N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-lmy48n-factory-80ab3689.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [LMY48N]">Link</a></td>
    <td>80ab3689617cd0fc1d352815a9bae2021ca0ee7c33fc2d3cd821bcb2b10af8e6</td>
  </tr>
  <tr id="fugumra58k">
    <td>6.0.0 (MRA58K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mra58k-factory-36637aa2.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MRA58K]">Link</a></td>
    <td>36637aa266810c8dfc38c7af9b50983c34535eecd975c562de24d73d453e45ea</td>
  </tr>
  <tr id="fugumra58n">
    <td>6.0.0 (MRA58N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mra58n-factory-3b5bccdc.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MRA58N]">Link</a></td>
    <td>3b5bccdc7ef95f4d8757da2a5a7806bad50c6c3407fc55f7b9940f7ae479fa8b</td>
  </tr>
  <tr id="fugummb29m">
    <td>6.0.1 (MMB29M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mmb29m-factory-203edd00.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MMB29M]">Link</a></td>
    <td>203edd000afc89c342e61e6ee2e8372bae8982fc779cf374d1ea7d7400241282</td>
  </tr>
  <tr id="fugummb29t">
    <td>6.0.1 (MMB29T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mmb29t-factory-80953b19.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MMB29T]">Link</a></td>
    <td>80953b195520cf153dd82122a210610b2a64ff4a0d4803a0379c42675e33bdd3</td>
  </tr>
  <tr id="fugummb29u">
    <td>6.0.1 (MMB29U)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mmb29u-factory-b97861b2.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MMB29U]">Link</a></td>
    <td>b97861b28b239bbd6ccebb8e6a09db4aa1f17d90e82842e7e590d9f0831f3dbd</td>
  </tr>
  <tr id="fugummb29v">
    <td>6.0.1 (MMB29V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mmb29v-factory-be9d09b4.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MMB29V]">Link</a></td>
    <td>be9d09b4378f9a3274ce4ad7a45d5535823b556df30c6654a394d9748f3f5b2b</td>
  </tr>
  <tr id="fugumob30d">
    <td>6.0.1 (MOB30D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mob30d-factory-b89b3606.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MOB30D]">Link</a></td>
    <td>b89b36063035bd8a650b86eaa629ab798be15fca543ebb5739efce3638bf6fa9</td>
  </tr>
  <tr id="fugumob30g">
    <td>6.0.1 (MOB30G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mob30g-factory-273c6d21.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MOB30G]">Link</a></td>
    <td>273c6d218a0955a1b40a3ca2489313f8c5010a4da96f255c85539f9bcc1559c3</td>
  </tr>
  <tr id="fugumob30m">
    <td>6.0.1 (MOB30M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mob30m-factory-17465cb7.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MOB30M]">Link</a></td>
    <td>17465cb7c2f26ffca96fb83ab387d50cc41ebc4e9b5ed40ae173c0ca0a51f13d</td>
  </tr>
  <tr id="fugumob30p">
    <td>6.0.1 (MOB30P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mob30p-factory-a9127fa5.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MOB30P]">Link</a></td>
    <td>a9127fa513717ec7af4afecebd8014b352922a1e77eb068e07d479b78bb83585</td>
  </tr>
  <tr id="fugumob30w">
    <td>6.0.1 (MOB30W)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-mob30w-factory-a9242814.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [MOB30W]">Link</a></td>
    <td>a92428145f52d5c2ab6d6dfba142d91ca804fd1d14c083f393f7f3205dd72b94</td>
  </tr>
  <tr id="fugunrd90m">
    <td>7.0.0 (NRD90M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-nrd90m-factory-3b5f38ea.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [NRD90M]">Link</a></td>
    <td>3b5f38ea2d721136cf803e053e07c55c5a83780267f0897dd89a8840016bf385</td>
  </tr>
  <tr id="fugunrd90r">
    <td>7.0.0 (NRD90R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-nrd90r-factory-663a9f79.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [NRD90R]">Link</a></td>
    <td>663a9f79612b3a1e3710148c62e4c0a4513c0fea34953ebb8268d94567a9b817</td>
  </tr>
  <tr id="fugunrd91d">
    <td>7.0.0 (NRD91D, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-nrd91d-factory-60a7d0e5.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [NRD91D]">Link</a></td>
    <td>60a7d0e500bfb45471c38b5aa4cf936fc992dd084dde743d664580b1763b589a</td>
  </tr>
  <tr id="fugunrd91n">
    <td>7.0.0 (NRD91N, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-nrd91n-factory-c3105e53.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [NRD91N]">Link</a></td>
    <td>c3105e53fbb91bcaa022d678358a426399d1260c459d8078a23e408040705723</td>
  </tr>
  <tr id="fugunmf26j">
    <td>7.1.1 (NMF26J, Dec 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-nmf26j-factory-4dd61763.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [NMF26J]">Link</a></td>
    <td>4dd61763120d981caf22b2abbd3dad3e4f76229eee503b8aea873f9cdb7da255</td>
  </tr>
  <tr id="fugunmf26r">
    <td>7.1.1 (NMF26R, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-nmf26r-factory-ab8fe2f8.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [NMF26R]">Link</a></td>
    <td>ab8fe2f85e521640aaaeba566030175ea1d3fdf1b77c23537338d596146485ae</td>
  </tr>
  <tr id="fugunmf26x">
    <td>7.1.1 (NMF26X, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-nmf26x-factory-ace86f3e.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [NMF26X]">Link</a></td>
    <td>ace86f3e26d5b4d623dcf9a5629ca45b23c8da2c70bb8800535e0eec75519299</td>
  </tr>
  <tr id="fugunmf27d">
    <td>7.1.1 (NMF27D, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-nmf27d-factory-55ddcf4e.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [NMF27D]">Link</a></td>
    <td>55ddcf4e5f08f61a4b659a9a98953e671da884fda47f33a9cbab5b1beaaf75c8</td>
  </tr>
  <tr id="fugun2g47h">
    <td>7.1.2 (N2G47H, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-n2g47h-factory-303349c6.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [N2G47H]">Link</a></td>
    <td>303349c6eebb9b9ce116102d7344326dde7e5ccb1fc685d98fc96e755d3d3898</td>
  </tr>
  <tr id="fugun2g47r">
    <td>7.1.2 (N2G47R, May 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-n2g47r-factory-bd937e40.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [N2G47R]">Link</a></td>
    <td>bd937e40d191d55c3948aa7caee39091e9c4e3d8b155fd8c8a15731f9ce8d98e</td>
  </tr>
  <tr id="fugun2g47x">
    <td>7.1.2 (N2G47X, Jun 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-n2g47x-factory-bf5df918.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [N2G47X]">Link</a></td>
    <td>bf5df918f463f815781e230b0a0fc74ca57a57ed58b29f4d14a6a24e2a955aef</td>
  </tr>
  <tr id="fugun2g48b">
    <td>7.1.2 (N2G48B, Jul 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-n2g48b-factory-fe2179ef.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [N2G48B]">Link</a></td>
    <td>fe2179ef2c58c589862a6e521c6c63e6567fdef2b4084a26ccb083ddf3edcb99</td>
  </tr>
  <tr id="fugun2g48c">
    <td>7.1.2 (N2G48C, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-n2g48c-factory-fa00f525.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [N2G48C]">Link</a></td>
    <td>fa00f5250df960e8adb51376580838e56b60349200b6cf46095b22a1942d425a</td>
  </tr>
  <tr id="fuguopr6.170623.021">
    <td>8.0.0 (OPR6.170623.021, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-opr6.170623.021-factory-e34311b0.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [OPR6.170623.021]">Link</a></td>
    <td>e34311b052e93b600bc217023f4b5b3d89db829acecb9dab962562fa3aa05996</td>
  </tr>
  <tr id="fuguopr2.170623.027">
    <td>8.0.0 (OPR2.170623.027, Nov 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/fugu-opr2.170623.027-factory-d4be396e.zip" class="gc-analytics-event" data-category="Android Images" data-label="fugu for Nexus Player [OPR2.170623.027]">Link</a></td>
    <td>d4be396ec7e1b569234eefe22b4a27234f45af22b8b59c47c5148ea160521fbe</td>
  </tr>
</tbody></table></div>

<h2 id="volantisg" is-upgraded="">"volantisg" for Nexus 9 (LTE)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="volantisglrx22c">
    <td>5.0.1 (LRX22C)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-lrx22c-factory-d8015ca4.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [LRX22C]">Link</a></td>
    <td>d8015ca4e9849fe90778be9c752a5b10f523be461b4aa4d0e651fbda2e75ad5c</td>
  </tr>
  <tr id="volantisglrx22l">
    <td>5.0.2 (LRX22L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-lrx22l-factory-cd3da569.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [LRX22L]">Link</a></td>
    <td>cd3da5697f5ff9c930c78c2eaa1c17ab2d899b15a5bf16783900cc9732ff1806</td>
  </tr>
  <tr id="volantisglmy47x">
    <td>5.1.1 (LMY47X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-lmy47x-factory-2a91598f.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [LMY47X]">Link</a></td>
    <td>2a91598fbb84dd8466684f964dee48953fc405d967d52e31c458ec8b80841aa8</td>
  </tr>
  <tr id="volantisglmy48i">
    <td>5.1.1 (LMY48I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-lmy48i-factory-898dfbd2.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [LMY48I]">Link</a></td>
    <td>898dfbd203defdf71629e9d0c715821256dec1124af57c6388652fce4f03ee87</td>
  </tr>
  <tr id="volantisglmy48m">
    <td>5.1.1 (LMY48M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-lmy48m-factory-88a64c37.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [LMY48M]">Link</a></td>
    <td>88a64c3719ed95447d6be74c8ecf9d4f9fe08372e8786b7734dccb93f5677f29</td>
  </tr>
  <tr id="volantisglmy48t">
    <td>5.1.1 (LMY48T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-lmy48t-factory-f7a4c096.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [LMY48T]">Link</a></td>
    <td>f7a4c09633b8e73c6cd0c04ec61ebebf7075123e7694009c14d63f08ec0230b2</td>
  </tr>
  <tr id="volantisglmy48x">
    <td>5.1.1 (LMY48X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-lmy48x-factory-f461d081.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [LMY48X]">Link</a></td>
    <td>f461d081a260d8e9d92e88f5efd80b802661477f78a9dc1d27aa1a791aff950f</td>
  </tr>
  <tr id="volantisglmy48z">
    <td>5.1.1 (LMY48Z)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-lmy48z-factory-e62889df.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [LMY48Z]">Link</a></td>
    <td>e62889df41c193b4e2da6257fc88ff5eb5aff82a8b1ce48ff0140fc11e18d0e3</td>
  </tr>
  <tr id="volantisglmy49f">
    <td>5.1.1 (LMY49F)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-lmy49f-factory-c9caeb4d.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [LMY49F]">Link</a></td>
    <td>c9caeb4d9888c9db4d473cc50ea8a75f125634da7e1c66d423114e1b675d3037</td>
  </tr>
  <tr id="volantisgmra58k">
    <td>6.0.0 (MRA58K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mra58k-factory-1dba8ee1.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MRA58K]">Link</a></td>
    <td>1dba8ee190a569583a73873734f06b70e1aeb2d7731b101a63a6651a26ed6d6f</td>
  </tr>
  <tr id="volantisgmra58n">
    <td>6.0.0 (MRA58N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mra58n-factory-d1194c11.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MRA58N]">Link</a></td>
    <td>d1194c114bf2adf985682661b5a5fa6dbba379af8845f1c32fc3168dab1b4277</td>
  </tr>
  <tr id="volantisgmmb29k">
    <td>6.0.1 (MMB29K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mmb29k-factory-ef7c9fd9.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MMB29K]">Link</a></td>
    <td>ef7c9fd9a339de16c3afa82d1eee18650ff4760648acd3d56d45da9db0928ee3</td>
  </tr>
  <tr id="volantisgmmb29s">
    <td>6.0.1 (MMB29S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mmb29s-factory-60e2b9e3.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MMB29S]">Link</a></td>
    <td>60e2b9e3837d5bbdd63e52a9ad54a3f45b20f34521e40d2fef8389872ea733a9</td>
  </tr>
  <tr id="volantisgmmb29r">
    <td>6.0.1 (MMB29R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mmb29r-factory-4048f881.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MMB29R]">Link</a></td>
    <td>4048f8815f4b489d475073333f780ed08fd022a5574d74cfc08423de9920bd42</td>
  </tr>
  <tr id="volantisgmmb29v">
    <td>6.0.1 (MMB29V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mmb29v-factory-2a546a9f.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MMB29V]">Link</a></td>
    <td>2a546a9ff09d57bc36858c5be4b7ca31357804735bbf382690b5b1e1bf3801aa</td>
  </tr>
  <tr id="volantisgmmb29x">
    <td>6.0.1 (MMB29X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mmb29x-factory-c2f54495.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MMB29X]">Link</a></td>
    <td>c2f54495871e70eea1b9e3cd21eba4057c7c9884b07a15f51b80d9fe9b4e2321</td>
  </tr>
  <tr id="volantisgmob30d">
    <td>6.0.1 (MOB30D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mob30d-factory-a6df6810.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MOB30D]">Link</a></td>
    <td>a6df68105124c7da8a196caa42cfbf18e4c23d3222e0a3f8475e3674365455fe</td>
  </tr>
  <tr id="volantisgmob30g">
    <td>6.0.1 (MOB30G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mob30g-factory-06932bb6.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MOB30G]">Link</a></td>
    <td>06932bb6c7a1d03a7842be6090a7719f9923a6d58f197b738ff3ebcda2ec5b21</td>
  </tr>
  <tr id="volantisgmob30m">
    <td>6.0.1 (MOB30M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mob30m-factory-7f1c6739.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MOB30M]">Link</a></td>
    <td>7f1c67390e186c4a671fdd4fddd8aadd45ffc9a1fb8f0feb09fad9ff4cd0ba7b</td>
  </tr>
  <tr id="volantisgmob30p">
    <td>6.0.1 (MOB30P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mob30p-factory-bd9c5e6b.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MOB30P]">Link</a></td>
    <td>bd9c5e6b3cf0ed1b20ba388afc457315443df5d3a78b3126db8c96f19fc09680</td>
  </tr>
  <tr id="volantisgmob30w">
    <td>6.0.1 (MOB30W)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mob30w-factory-1afbef6f.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MOB30W]">Link</a></td>
    <td>1afbef6f45df55708d431a293371c67f5dd991daca8ec7f4593f9d77e2abd2c6</td>
  </tr>
  <tr id="volantisgmob31e">
    <td>6.0.1 (MOB31E)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-mob31e-factory-b8c6b982.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [MOB31E]">Link</a></td>
    <td>b8c6b9821622934872b8c162808bb76b78c2b18fd0a99c90fa423b1a79c11dcf</td>
  </tr>
  <tr id="volantisgnrd90r">
    <td>7.0.0 (NRD90R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-nrd90r-factory-ba76b361.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [NRD90R]">Link</a></td>
    <td>ba76b3613888e17fd9b36382dbfb5f4cf3e7416a612fbbeb5b6197d73c9be56f</td>
  </tr>
  <tr id="volantisgnrd91n">
    <td>7.0.0 (NRD91N, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-nrd91n-factory-972fb42b.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [NRD91N]">Link</a></td>
    <td>972fb42bc769243968b833b2cae1f59082045392d548c63e3f675cf9fd51edac</td>
  </tr>
  <tr id="volantisgnmf26f">
    <td>7.1.1 (NMF26F, Dec 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-nmf26f-factory-cb15d790.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [NMF26F]">Link</a></td>
    <td>cb15d79007c1421b612fe6256268eb35c8ab2e7caa6ec4fa26be5b772bb5e117</td>
  </tr>
  <tr id="volantisgn4f26q">
    <td>7.1.1 (N4F26Q, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-n4f26q-factory-52cefc27.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [N4F26Q]">Link</a></td>
    <td>52cefc279dc73193125f7531c3e9a49852776411b41eca64b0095197d8471280</td>
  </tr>
  <tr id="volantisgn4f26t">
    <td>7.1.1 (N4F26T, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-n4f26t-factory-ac2cfe5f.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [N4F26T]">Link</a></td>
    <td>ac2cfe5fd43d98d6f9880bd5f1a7f6b5fb57ed187e52205f4650eeb6bc235c5e</td>
  </tr>
  <tr id="volantisgn4f26x">
    <td>7.1.1 (N4F26X, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-n4f26x-factory-5e0a6018.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [N4F26X]">Link</a></td>
    <td>5e0a6018465ffdb6bd97bb1680e3a59892f42d5580e63041c38baf29b75e06f7</td>
  </tr>
  <tr id="volantisgn4f27b">
    <td>7.1.1 (N4F27B, May 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-n4f27b-factory-c3edb21e.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [N4F27B]">Link</a></td>
    <td>c3edb21e3a1e278dce4318897498efdc132e32a65bc851d5a516010e00287c8f</td>
  </tr>
  <tr id="volantisgn4f27e">
    <td>7.1.1 (N4F27E, Jun 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-n4f27e-factory-e29015b9.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [N4F27E]">Link</a></td>
    <td>e29015b9b6d5cb7e1f3f525c5e3bc7591865e80eed2111c479b63726a4d3f0f8</td>
  </tr>
  <tr id="volantisgn4f27i">
    <td>7.1.1 (N4F27I, Jul 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-n4f27i-factory-a7d03ede.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [N4F27I]">Link</a></td>
    <td>a7d03ede5b642f98b8450422ea36c6bcd0c42cdfbd5e255f720dae4606c69255</td>
  </tr>
  <tr id="volantisgn4f27k">
    <td>7.1.1 (N4F27K, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-n4f27k-factory-a69e5f5e.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [N4F27K]">Link</a></td>
    <td>a69e5f5e2535b9789998990f0138521d75761c463e70b0365f6c2ef78cd16574</td>
  </tr>
  <tr id="volantisgn4f27o">
    <td>7.1.1 (N4F27O, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-n4f27o-factory-6826050e.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [N4F27O]">Link</a></td>
    <td>6826050ed70173fcdde8cf861f4c3f081f638f2a12b98ee93f7271dc1c72ec08</td>
  </tr>
  <tr id="volantisgn4f27p">
    <td>7.1.1 (N4F27P, Oct 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantisg-n4f27p-factory-1e29c858.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantisg for Nexus 9 (LTE) [N4F27P]">Link</a></td>
    <td>1e29c858d283d75dab5c53eaa6397cd1f8bf4b3dd24efa03fb4b6f153eb899ac</td>
  </tr>
</tbody></table></div>

<h2 id="volantis" is-upgraded="">"volantis" for Nexus 9 (Wi-Fi)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="volantislrx21q">
    <td>5.0 (LRX21Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-lrx21q-factory-90cce0e6.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [LRX21Q]">Link</a></td>
    <td>90cce0e6f02263122b4ed59ce8f8938d714ebae5febf41e36968aee9de385b99</td>
  </tr>
  <tr id="volantislrx21r">
    <td>5.0 (LRX21R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-lrx21r-factory-d72d6d1a.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [LRX21R]">Link</a></td>
    <td>d72d6d1a3f8f8ae3c6598dbec46ad6f8418341604ddace5ca3a1d5eaf2157e18</td>
  </tr>
  <tr id="volantislrx22c">
    <td>5.0.1 (LRX22C)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-lrx22c-factory-cd4320b7.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [LRX22C]">Link</a></td>
    <td>cd4320b7ee3d992901d31bba4a86e8f0575cb2a57feea3d3999d9865be125f55</td>
  </tr>
  <tr id="volantislrx22l">
    <td>5.0.2 (LRX22L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-lrx22l-factory-0e950403.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [LRX22L]">Link</a></td>
    <td>0e950403538452b615dc6a8145445c7a243d46d11e27bbc833fbfa5187c6c1ea</td>
  </tr>
  <tr id="volantislmy47x">
    <td>5.1.1 (LMY47X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-lmy47x-factory-10914332.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [LMY47X]">Link</a></td>
    <td>1091433202f01ef83176d5afbbf70e64307038f0a8328e06e5597760361dc973</td>
  </tr>
  <tr id="volantislmy48i">
    <td>5.1.1 (LMY48I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-lmy48i-factory-ff3f2f81.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [LMY48I]">Link</a></td>
    <td>ff3f2f812df09f460ef10610eef0533cc0050239a09b1ad557fd6132817376db</td>
  </tr>
  <tr id="volantislmy48m">
    <td>5.1.1 (LMY48M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-lmy48m-factory-13484746.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [LMY48M]">Link</a></td>
    <td>1348474657d40374a3b44b5980889af887c07ae9353040edb50aa9e5799f1692</td>
  </tr>
  <tr id="volantislmy48t">
    <td>5.1.1 (LMY48T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-lmy48t-factory-b925de62.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [LMY48T]">Link</a></td>
    <td>b925de62459c521e6c09c69424a89b699c6f25c1ff5abab740fe86cc530b76e5</td>
  </tr>
  <tr id="volantismra58k">
    <td>6.0.0 (MRA58K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mra58k-factory-1fc6a923.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MRA58K]">Link</a></td>
    <td>1fc6a92388dcb946e4a2f6747ab70b0493b024cdfb3ffa0a6f577c6890516fee</td>
  </tr>
  <tr id="volantismra58n">
    <td>6.0.0 (MRA58N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mra58n-factory-77facd1e.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MRA58N]">Link</a></td>
    <td>77facd1e6473e088fd6103e6d1be842a095fc58014e30f62bc06b3011f060e22</td>
  </tr>
  <tr id="volantismmb29k">
    <td>6.0.1 (MMB29K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mmb29k-factory-0987fac3.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MMB29K]">Link</a></td>
    <td>0987fac30ebffe1bd61daac825c7d8af46562b7b13ffce1ce9015cb99c36c708</td>
  </tr>
  <tr id="volantismmb29s">
    <td>6.0.1 (MMB29S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mmb29s-factory-c1f746d3.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MMB29S]">Link</a></td>
    <td>c1f746d3333cf8afa40eef744f6c91fcb52ff5b6f14cbff677e382e1f2406d81</td>
  </tr>
  <tr id="volantismmb29r">
    <td>6.0.1 (MMB29R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mmb29r-factory-bffa6ff7.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MMB29R]">Link</a></td>
    <td>bffa6ff738af18fe41973af19d18fd00ef7a793c5020a6210c75bb6adcc0bbca</td>
  </tr>
  <tr id="volantismmb29v">
    <td>6.0.1 (MMB29V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mmb29v-factory-da6c22ad.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MMB29V]">Link</a></td>
    <td>da6c22ad9f77e1801d8a6b37d3690499fbfa1dd2939a127f4a9dab057da4c6b7</td>
  </tr>
  <tr id="volantismob30d">
    <td>6.0.1 (MOB30D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mob30d-factory-391d89ed.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MOB30D]">Link</a></td>
    <td>391d89eda3e69d2f0beb6f5460395af016b28bca181e79d5d8e40a8e4a0a6892</td>
  </tr>
  <tr id="volantismob30g">
    <td>6.0.1 (MOB30G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mob30g-factory-1c35d799.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MOB30G]">Link</a></td>
    <td>1c35d7992486d3f565eb7f1d20ccd1ef675c6fd8fe8c41ae798503ce4cb143b8</td>
  </tr>
  <tr id="volantismob30m">
    <td>6.0.1 (MOB30M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mob30m-factory-adffa5c1.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MOB30M]">Link</a></td>
    <td>adffa5c14830ad2eae3ab4f616868e9311cc8cbfc653ba2abf200d9441e614d8</td>
  </tr>
  <tr id="volantismob30p">
    <td>6.0.1 (MOB30P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mob30p-factory-a742a212.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MOB30P]">Link</a></td>
    <td>a742a2124f5e4e1fe8b4ea1db007698a9359a8e45215b320b4b388b73e41d551</td>
  </tr>
  <tr id="volantismob30w">
    <td>6.0.1 (MOB30W)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-mob30w-factory-c2c750bc.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [MOB30W]">Link</a></td>
    <td>c2c750bcd815a48ce061deae94a43ce156de0f5a97f5e7b59f9f96502fd740a9</td>
  </tr>
  <tr id="volantisnrd90m">
    <td>7.0.0 (NRD90M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-nrd90m-factory-fccddb6d.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [NRD90M]">Link</a></td>
    <td>fccddb6d82bd0c21b5200d047b24b6b5a6af798aa788540e1b607cc7a49a943b</td>
  </tr>
  <tr id="volantisnrd90r">
    <td>7.0.0 (NRD90R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-nrd90r-factory-84de678f.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [NRD90R]">Link</a></td>
    <td>84de678f9f4b5b96f2f44dfba0ef0794a56e3727c11e410fb0f485f545083c78</td>
  </tr>
  <tr id="volantisnrd91d">
    <td>7.0.0 (NRD91D, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-nrd91d-factory-a27db9bc.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [NRD91D]">Link</a></td>
    <td>a27db9bc4613f5fc41ce30372ce8401d445bee46358517389dbcfd0fa4de1289</td>
  </tr>
  <tr id="volantisnrd91n">
    <td>7.0.0 (NRD91N, Nov 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-nrd91n-factory-97ea58be.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [NRD91N]">Link</a></td>
    <td>97ea58bec951f11bf1ffff892ef0a8de746e9ae92a0657b90a305e4e58624fee</td>
  </tr>
  <tr id="volantisnmf26f">
    <td>7.1.1 (NMF26F, Dec 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-nmf26f-factory-dcb1615a.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [NMF26F]">Link</a></td>
    <td>dcb1615a22931332a1f2a7a352e4fb04f116c7f43dd86f2ae737714117339aa1</td>
  </tr>
  <tr id="volantisn4f26m">
    <td>7.1.1 (N4F26M, Jan 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n4f26m-factory-c8b6741d.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N4F26M]">Link</a></td>
    <td>c8b6741d3327ecda89c8cd47625eff4ff213b3e00573e5fd291934b6979f06d1</td>
  </tr>
  <tr id="volantisn4f26q">
    <td>7.1.1 (N4F26Q, Feb 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n4f26q-factory-2207298d.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N4F26Q]">Link</a></td>
    <td>2207298d3ef06cba1367a9e1fe4d7bf2483ed7e8dd6b735136ad9f448ec0ff3a</td>
  </tr>
  <tr id="volantisn4f26t">
    <td>7.1.1 (N4F26T, Mar 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n4f26t-factory-641764b5.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N4F26T]">Link</a></td>
    <td>641764b5643de7fb87d5333ceb35ab367cd3031f7fea7a0d0367c9dd1492108f</td>
  </tr>
  <tr id="volantisn4f26x">
    <td>7.1.1 (N4F26X, Apr 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n4f26x-factory-788661ae.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N4F26X]">Link</a></td>
    <td>788661ae86059575497edf290d714d92b2fb544502235bcef9a31841a0369899</td>
  </tr>
  <tr id="volantisn4f27b">
    <td>7.1.1 (N4F27B, May 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n4f27b-factory-f171c46f.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N4F27B]">Link</a></td>
    <td>f171c46f88694d3246d9dfa7387e7566a892825c01e6762c70a98d8014fb35b5</td>
  </tr>
  <tr id="volantisn9f27c">
    <td>7.1.1 (N9F27C, Jun 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n9f27c-factory-0d0540fb.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N9F27C]">Link</a></td>
    <td>0d0540fbc57f29ca22b13fbb0564330f0b84178ccf1f6b2c6f32a4ec0a7cc658</td>
  </tr>
  <tr id="volantisn9f27f">
    <td>7.1.1 (N9F27F, Jul 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n9f27f-factory-265c20e8.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N9F27F]">Link</a></td>
    <td>265c20e87359a6865c8edaa33510b36fce1c0b6b9f5936d8c30a9da7d6f5a2bf</td>
  </tr>
  <tr id="volantisn9f27h">
    <td>7.1.1 (N9F27H, Aug 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n9f27h-factory-d2ad51d6.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N9F27H]">Link</a></td>
    <td>d2ad51d621a60f903e3080a3ea648e6eb53a1eab5c26662c0bf2970eacb002c3</td>
  </tr>
  <tr id="volantisn9f27l">
    <td>7.1.1 (N9F27L, Sep 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n9f27l-factory-f8ffc0da.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N9F27L]">Link</a></td>
    <td>f8ffc0dabae79a8ac7608c57973b4ba148152fa9e0c6820b81e6376087847f75</td>
  </tr>
  <tr id="volantisn9f27m">
    <td>7.1.1 (N9F27M, Oct 2017)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/volantis-n9f27m-factory-a0d47736.zip" class="gc-analytics-event" data-category="Android Images" data-label="volantis for Nexus 9 (Wi-Fi) [N9F27M]">Link</a></td>
    <td>a0d4773612f987fbff27b8eb0b4d94f17912e42e50ad7f6230d7b55f760ece8e</td>
  </tr>
</tbody></table></div>

<h2 id="hammerhead" is-upgraded="">"hammerhead" for Nexus 5 (GSM/LTE)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="hammerheadkrt16m">
    <td>4.4 (KRT16M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-krt16m-factory-fb4041cc.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [KRT16M]">Link</a></td>
    <td>fb4041cc77a51c2f8c93afcc06df4c50e029fef6441e1b794be495be9cf29efc</td>
  </tr>
  <tr id="hammerheadkot49h">
    <td>4.4.2 (KOT49H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-kot49h-factory-3c5d358b.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [KOT49H]">Link</a></td>
    <td>3c5d358ba25ee32afc1b2fc9d7d7abbc8515f241f073a292da28e668c9ef6efb</td>
  </tr>
  <tr id="hammerheadktu84m">
    <td>4.4.3 (KTU84M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-ktu84m-factory-9c4610fb.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [KTU84M]">Link</a></td>
    <td>9c4610fb1964618685c099934784057bc13de4d3c1c34d70881b5fe7cd786382</td>
  </tr>
  <tr id="hammerheadktu84p">
    <td>4.4.4 (KTU84P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-ktu84p-factory-1f5f26b1.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [KTU84P]">Link</a></td>
    <td>1f5f26b17be1bb63874d82cdb03a8dea70fcff5dd971f07e6aa6669123e4f8ce</td>
  </tr>
  <tr id="hammerheadktu84q">
    <td>4.4.4 Release 2 (For 2Degrees/NZ, Telstra/AUS and India ONLY) (KTU84Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-ktu84q-factory-654c5471.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [KTU84Q]">Link</a></td>
    <td>654c5471bbb866193e571b9ac74da25bf436e21a8ee1f0f4af8fd06ad01e2f61</td>
  </tr>
  <tr id="hammerheadlrx21o">
    <td>5.0 (LRX21O)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-lrx21o-factory-56a09d43.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [LRX21O]">Link</a></td>
    <td>56a09d43d0dcc808d9dd9e2ed4c424af29bec2b5f343632d6ad0386b2dfcf854</td>
  </tr>
  <tr id="hammerheadlrx22c">
    <td>5.0.1 (LRX22C)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-lrx22c-factory-3b22f481.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [LRX22C]">Link</a></td>
    <td>3b22f4819d718818a65582c5c904073847b66227608f7485719935105a7e5b69</td>
  </tr>
  <tr id="hammerheadlmy47d">
    <td>5.1.0 (LMY47D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-lmy47d-factory-7df990ed.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [LMY47D]">Link</a></td>
    <td>7df990ed37728f44f4c77d1c42c306df802f61497799bde73168b17d89c6b6fc</td>
  </tr>
  <tr id="hammerheadlmy47i">
    <td>5.1.0 (LMY47I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-lmy47i-factory-f1734da1.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [LMY47I]">Link</a></td>
    <td>f1734da163304f57b23f43d79755abec60e286ddfecacb95419ff5d642bcc7a1</td>
  </tr>
  <tr id="hammerheadlmy48b">
    <td>5.1.1 (LMY48B)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-lmy48b-factory-e90640d2.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [LMY48B]">Link</a></td>
    <td>e90640d2c2b53f9cad26addbefa42ef54d48002f0a0f95bec3bc92b161d2ffe3</td>
  </tr>
  <tr id="hammerheadlmy48i">
    <td>5.1.1 (LMY48I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-lmy48i-factory-67766277.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [LMY48I]">Link</a></td>
    <td>67766277bfc9db722d8d7837ef205bda492476101d45160a37525b0b27af4352</td>
  </tr>
  <tr id="hammerheadlmy48m">
    <td>5.1.1 (LMY48M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-lmy48m-factory-e01ca3b7.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [LMY48M]">Link</a></td>
    <td>e01ca3b73688ee06e83d6a133369f8e254b3a64ce6fe85a491534d937b9848df</td>
  </tr>
  <tr id="hammerheadmra58k">
    <td>6.0.0 (MRA58K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mra58k-factory-ccbc4611.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MRA58K]">Link</a></td>
    <td>ccbc4611deaa6e35a77b700843f7ad0e74a72fd197d3a974d51058d4bb0d31e3</td>
  </tr>
  <tr id="hammerheadmra58n">
    <td>6.0.0 (MRA58N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mra58n-factory-30da525d.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MRA58N]">Link</a></td>
    <td>30da525dd8aa256a796aebd0aafb030cbef584ed90cb64fb383f8ce4b79054e6</td>
  </tr>
  <tr id="hammerheadmmb29k">
    <td>6.0.1 (MMB29K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mmb29k-factory-e5796b14.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MMB29K]">Link</a></td>
    <td>e5796b1407d0c3ee6b8c01468bed0f01ddaa6204db60cbce1a6c55ebd77434c4</td>
  </tr>
  <tr id="hammerheadmmb29s">
    <td>6.0.1 (MMB29S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mmb29s-factory-82c3474f.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MMB29S]">Link</a></td>
    <td>82c3474fc87298f160e0e512c6d32458568a3057c28caa333a97dbb773d6a6cf</td>
  </tr>
  <tr id="hammerheadmmb29q">
    <td>6.0.1 (MMB29Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mmb29q-factory-27d8a4a5.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MMB29Q]">Link</a></td>
    <td>27d8a4a55de5613b98985f71eeb85384d0a78aaf2ac372f56a2d08eef92fd8f5</td>
  </tr>
  <tr id="hammerheadmmb29v">
    <td>6.0.1 (MMB29V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mmb29v-factory-7f1b9c7e.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MMB29V]">Link</a></td>
    <td>7f1b9c7ed1df6124b935ae1fd2543f814b182349e1852506e5bd5bdb417ecee7</td>
  </tr>
  <tr id="hammerheadmmb29x">
    <td>6.0.1 (MMB29X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mmb29x-factory-9ebfbf54.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MMB29X]">Link</a></td>
    <td>9ebfbf5473e00a25ec832b4e67c210f087aefe16b97b9b0f9d780e6d3131ab35</td>
  </tr>
  <tr id="hammerheadmob30d">
    <td>6.0.1 (MOB30D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mob30d-factory-43d1482d.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MOB30D]">Link</a></td>
    <td>43d1482d8771f5b5d97f54b19e84481651357b6e8f98a719a9b3d56a0026a5db</td>
  </tr>
  <tr id="hammerheadmob30h">
    <td>6.0.1 (MOB30H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mob30h-factory-2c178ff7.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MOB30H]">Link</a></td>
    <td>2c178ff79014fd5703d423020d22df4618b192a9af9283c60105e88300c5aeb2</td>
  </tr>
  <tr id="hammerheadmob30m">
    <td>6.0.1 (MOB30M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mob30m-factory-af019693.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MOB30M]">Link</a></td>
    <td>af019693798dceac03879feb3f46ee5b63802081c649d8bee821277d204c1810</td>
  </tr>
  <tr id="hammerheadmob30p">
    <td>6.0.1 (MOB30P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mob30p-factory-8d36be0c.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MOB30P]">Link</a></td>
    <td>8d36be0cfcc28da4986da0a211403b2586ab90078f995891eaea608891d98ddc</td>
  </tr>
  <tr id="hammerheadmob30y">
    <td>6.0.1 (MOB30Y)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mob30y-factory-5bea6457.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MOB30Y]">Link</a></td>
    <td>5bea645798a9584f6b06419537befbbb41d0578a96b5c889f7a6d8c02e9d0962</td>
  </tr>
  <tr id="hammerheadmob31e">
    <td>6.0.1 (MOB31E)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-mob31e-factory-90504514.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [MOB31E]">Link</a></td>
    <td>9050451400a69d8cd6e2b559e87c052bb7e8d7482640da18c39f25f30dba7d7d</td>
  </tr>
  <tr id="hammerheadm4b30x">
    <td>6.0.1 (M4B30X, Oct 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-m4b30x-factory-10cfaa5c.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [M4B30X]">Link</a></td>
    <td>10cfaa5c8ff1753af20283f5e5f938ddebbad094c4e22aadbd925ecdc806e8b3</td>
  </tr>
  <tr id="hammerheadm4b30z">
    <td>6.0.1 (M4B30Z, Dec 2016)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/hammerhead-m4b30z-factory-625c027b.zip" class="gc-analytics-event" data-category="Android Images" data-label="hammerhead for Nexus 5 (GSM/LTE) [M4B30Z]">Link</a></td>
    <td>625c027b21afe6de7c3d0de66e3a42000269dd00c2ef9a5347007734537f3ea2</td>
  </tr>
</tbody></table></div>

<h2 id="razor" is-upgraded="">"razor" for Nexus 7 [2013] (Wi-Fi)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="razorjss15q">
    <td>4.3 (JSS15Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-jss15q-factory-e5793513.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [JSS15Q]">Link</a></td>
    <td>e5793513cac2602f5943b162a3693ea44f3a793187943edbcd94a6474894c308</td>
  </tr>
  <tr id="razorjss15r">
    <td>4.3 (JSS15R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-jss15r-factory-10bb907c.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [JSS15R]">Link</a></td>
    <td>10bb907c4f7f465d0bcd7910b63485835f673d891b28c12629dd15db6d37d962</td>
  </tr>
  <tr id="razorkrt16s">
    <td>4.4 (KRT16S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-krt16s-factory-cb470f70.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [KRT16S]">Link</a></td>
    <td>cb470f70e8e4c560fa0fa511806e73b12179c81fe4304adec623227a1a948a65</td>
  </tr>
  <tr id="razorkot49h">
    <td>4.4.2 (KOT49H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-kot49h-factory-a3f2c6ab.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [KOT49H]">Link</a></td>
    <td>a3f2c6ab42e84796726102771e6a0ea1045e8bc42e51085105b6a06295dea1af</td>
  </tr>
  <tr id="razorktu84l">
    <td>4.4.3 (KTU84L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-ktu84l-factory-99920590.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [KTU84L]">Link</a></td>
    <td>99920590cd68095b4110a3930d45212b73d01ba6fc147b6f1192094eacae881a</td>
  </tr>
  <tr id="razorktu84p">
    <td>4.4.4 (KTU84P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-ktu84p-factory-2482a7d5.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [KTU84P]">Link</a></td>
    <td>2482a7d5d363da6c4beeb2ca35d05934ccc32e70484dd089d81f79438d908e91</td>
  </tr>
  <tr id="razorlrx21p">
    <td>5.0 (LRX21P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-lrx21p-factory-f6f1633a.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [LRX21P]">Link</a></td>
    <td>f6f1633af1d87d27b360188f60d8e047158e362ca2be53c66754df4a7d586bd0</td>
  </tr>
  <tr id="razorlrx22c">
    <td>5.0.1 (LRX22C)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-lrx22c-factory-b8489e3a.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [LRX22C]">Link</a></td>
    <td>b8489e3abf8c25544f0a688ff60dfa544c3bfcf2387bb537b06e3fd408b17c48</td>
  </tr>
  <tr id="razorlrx22g">
    <td>5.0.2 (LRX22G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-lrx22g-factory-980d1360.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [LRX22G]">Link</a></td>
    <td>980d1360ab8ea0dcb9550b4f25a8b7bda726efb0a6d95caa3347d42b1bc00b57</td>
  </tr>
  <tr id="razorlmy47o">
    <td>5.1.0 (LMY47O)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-lmy47o-factory-06605773.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [LMY47O]">Link</a></td>
    <td>066057739801c9401e8017c6e655867fbbd1f93f6c0798ed3845ffa60334d3d8</td>
  </tr>
  <tr id="razorlmy47v">
    <td>5.1.1 (LMY47V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-lmy47v-factory-18ea5082.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [LMY47V]">Link</a></td>
    <td>18ea508292bd284b4bacebe1b165016b384ab943f4fed2313ae14d9596972917</td>
  </tr>
  <tr id="razorlmy48g">
    <td>5.1.1 (LMY48G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-lmy48g-factory-241edd58.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [LMY48G]">Link</a></td>
    <td>241edd58ebf1676d34676f55959772f1f886adaed005dd1ac114039dd67dde7a</td>
  </tr>
  <tr id="razorlmy48i">
    <td>5.1.1 (LMY48I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-lmy48i-factory-deb25f22.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [LMY48I]">Link</a></td>
    <td>deb25f226e98f0f1d4e50fc2a1770bf5f3a0183f67f803bd2192c079585f97cf</td>
  </tr>
  <tr id="razorlmy48m">
    <td>5.1.1 (LMY48M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-lmy48m-factory-7f8241f5.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [LMY48M]">Link</a></td>
    <td>7f8241f52fd0c9c43a67f04efae54f190314f6583cf6c292bf9a4f61206d3584</td>
  </tr>
  <tr id="razorlmy48t">
    <td>5.1.1 (LMY48T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-lmy48t-factory-0db13100.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [LMY48T]">Link</a></td>
    <td>0db131001ec2a7af3633a0eb12756000032095d5c6314dec2b5d9e916e70980a</td>
  </tr>
  <tr id="razormra58k">
    <td>6.0.0 (MRA58K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mra58k-factory-7b438d31.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MRA58K]">Link</a></td>
    <td>7b438d31eb3b50e008b2d8183dda864523aaab38032e219e017956af2d7676e2</td>
  </tr>
  <tr id="razormra58u">
    <td>6.0.0 (MRA58U)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mra58u-factory-17f59671.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MRA58U]">Link</a></td>
    <td>17f5967104ce9ac95eff76ec71806f521bd8309f49ae5ea064970e3241b38636</td>
  </tr>
  <tr id="razormra58v">
    <td>6.0.0 (MRA58V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mra58v-factory-d3d8bc1f.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MRA58V]">Link</a></td>
    <td>d3d8bc1f9f45bc485e9938dbfaec3d908c910352b8dd4f1d93b8cb971691e562</td>
  </tr>
  <tr id="razormmb29k">
    <td>6.0.1 (MMB29K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mmb29k-factory-8b43affc.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MMB29K]">Link</a></td>
    <td>8b43affc42eff296512156a982cdf9bba7373a891ba346f7c23f1903eb9b6afd</td>
  </tr>
  <tr id="razormmb29o">
    <td>6.0.1 (MMB29O)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mmb29o-factory-edef049a.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MMB29O]">Link</a></td>
    <td>edef049a5a768ca1c9aac9f48ee53f716117ded8ef7b6b18db51d077e95a08a3</td>
  </tr>
  <tr id="razormmb29q">
    <td>6.0.1 (MMB29Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mmb29q-factory-1fc8bb0c.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MMB29Q]">Link</a></td>
    <td>1fc8bb0c360426dd5bc745caf32c9f7451a66d707147a2991e5de43973eea947</td>
  </tr>
  <tr id="razormmb29v">
    <td>6.0.1 (MMB29V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mmb29v-factory-97ce617e.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MMB29V]">Link</a></td>
    <td>97ce617ec127e8de5c96ac552773d683210029df4f082539fbd3ab449be42f4a</td>
  </tr>
  <tr id="razormob30d">
    <td>6.0.1 (MOB30D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mob30d-factory-8e8b2ba7.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MOB30D]">Link</a></td>
    <td>8e8b2ba7d0f014963a8e41cdc50ed82be428a9e49ed75dc0d1d6a3abb978d5b1</td>
  </tr>
  <tr id="razormob30j">
    <td>6.0.1 (MOB30J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mob30j-factory-58203981.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MOB30J]">Link</a></td>
    <td>582039814fd8b15f87760648ddb33e3412771cae1c687775677a9d0ffaed6a92</td>
  </tr>
  <tr id="razormob30m">
    <td>6.0.1 (MOB30M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mob30m-factory-4890ef1d.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MOB30M]">Link</a></td>
    <td>4890ef1d9b1b5ec82e743f5433386fab7f8daff4f83ac7c07c5a054377c4056e</td>
  </tr>
  <tr id="razormob30p">
    <td>6.0.1 (MOB30P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mob30p-factory-2780fa5e.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MOB30P]">Link</a></td>
    <td>2780fa5e07fcdc427aceb85fd78d9a205290b8bcd9f20fd3c1a145ec6985669a</td>
  </tr>
  <tr id="razormob30x">
    <td>6.0.1 (MOB30X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razor-mob30x-factory-52684dff.zip" class="gc-analytics-event" data-category="Android Images" data-label="razor for Nexus 7 [2013] (Wi-Fi) [MOB30X]">Link</a></td>
    <td>52684dffb1683ac1f012083e3476f2aad285ca937eaae1a88024ebaec1137339</td>
  </tr>
</tbody></table></div>

<h2 id="razorg" is-upgraded="">"razorg" for Nexus 7 [2013] (Mobile)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="razorgjls36c">
    <td>4.3 (JLS36C)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-JLS36C-factory-834eab41.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [JLS36C]">Link</a></td>
    <td>834eab41c8021d9016b8d7b5324ad993c655f918f7c3a42ee967d06c60565c40</td>
  </tr>
  <tr id="razorgjls36i">
    <td>4.3.1 (JLS36I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-jls36i-factory-c7819e38.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [JLS36I]">Link</a></td>
    <td>c7819e38d0beef181c864973a7cb889e20b50b2dd112c48d37979a9f8e7f7c82</td>
  </tr>
  <tr id="razorgkrt16s">
    <td>4.4 (KRT16S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-krt16s-factory-4c0e2bbf.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [KRT16S]">Link</a></td>
    <td>4c0e2bbfa073d76a9582e8d2f54fa8dda2c78eddd72cac16bafe3371f3d10d28</td>
  </tr>
  <tr id="razorgkot49h">
    <td>4.4.2 (KOT49H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-kot49h-factory-67f0f487.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [KOT49H]">Link</a></td>
    <td>67f0f487b1ca70376a9a6406abe5cfcfb713d47505502b8aa6326f9ca50c28f8</td>
  </tr>
  <tr id="razorgkvt49l">
    <td>4.4.2_r2 (Verizon) (KVT49L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-kvt49l-factory-6cf4006d.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [KVT49L]">Link</a></td>
    <td>6cf4006d16d39ec27d0f3f3481257b8665c3b744c03bff6879f6c5474a611477</td>
  </tr>
  <tr id="razorgktu84l">
    <td>4.4.3 (KTU84L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-ktu84l-factory-23a28047.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [KTU84L]">Link</a></td>
    <td>23a280475cecb776484dcaccb4067916850e6b63a7ff5c2d483ce5e1b7540743</td>
  </tr>
  <tr id="razorgktu84p">
    <td>4.4.4 (KTU84P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-ktu84p-factory-d0c428e1.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [KTU84P]">Link</a></td>
    <td>d0c428e1592fa6bbe252ba07dbacc65c8951106d1759bf4384b97c5f1b8ae460</td>
  </tr>
  <tr id="razorglrx22g">
    <td>5.0.2 (LRX22G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-lrx22g-factory-c4fed480.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [LRX22G]">Link</a></td>
    <td>c4fed480298d9b6404dccf5a513495cabf567970db8299340acac1f11f66e675</td>
  </tr>
  <tr id="razorglmy47o">
    <td>5.1.0 (LMY47O)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-lmy47o-factory-9db6efe6.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [LMY47O]">Link</a></td>
    <td>9db6efe6c5957f1d1b9f74c6eb409bfd81c0ae8a4d346d8fc4a6dd74e4731a9d</td>
  </tr>
  <tr id="razorglmy47v">
    <td>5.1.1 (LMY47V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-lmy47v-factory-d141b515.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [LMY47V]">Link</a></td>
    <td>d141b515f3296f0a6b25858d1fe375edbc74224d41a394227a4f65bfdab927c6</td>
  </tr>
  <tr id="razorglmy48p">
    <td>5.1.1 (LMY48P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-lmy48p-factory-c3dc516c.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [LMY48P]">Link</a></td>
    <td>c3dc516cb278b55e17c9be513be6c162d27ddcd417baa9139e33f582d99f19cc</td>
  </tr>
  <tr id="razorglmy48u">
    <td>5.1.1 (LMY48U)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-lmy48u-factory-96decafd.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [LMY48U]">Link</a></td>
    <td>96decafd96a1c5b6f131b8226499316a0da783299f70118116fca5ee2011b004</td>
  </tr>
  <tr id="razorglmy48x">
    <td>5.1.1 (LMY48X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-lmy48x-factory-0d952c83.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [LMY48X]">Link</a></td>
    <td>0d952c83d9cfd3547a027af5f418f4a3b22cb172e727f033dce9de47737ba2ab</td>
  </tr>
  <tr id="razorglmy48z">
    <td>5.1.1 (LMY48Z)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-lmy48z-factory-9a4845b2.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [LMY48Z]">Link</a></td>
    <td>9a4845b2481e1ee24403c77c90daeee04d71ee3233ebed98972b9e23dfb953ce</td>
  </tr>
  <tr id="razorgmra58k">
    <td>6.0.0 (MRA58K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mra58k-factory-0f5a7c20.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MRA58K]">Link</a></td>
    <td>0f5a7c205a5ba7b386266c76c40d0d51a73f87ef24600440a1aa3b6e523bf2b5</td>
  </tr>
  <tr id="razorgmra58n">
    <td>6.0.0 (MRA58N)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mra58n-factory-53fbc37c.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MRA58N]">Link</a></td>
    <td>53fbc37c464be17d00dc4968a390269379b3135cdfeccf83dd93fe8f523560e9</td>
  </tr>
  <tr id="razorgmra58v">
    <td>6.0.0 (MRA58V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mra58v-factory-0811c13a.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MRA58V]">Link</a></td>
    <td>0811c13a4bc348c21de5168c54d996688705c6f554ecd6e5112885c02f7e530b</td>
  </tr>
  <tr id="razorgmra59b">
    <td>6.0.0 (MRA59B)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mra59b-factory-f4950bb4.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MRA59B]">Link</a></td>
    <td>f4950bb48808f27624239600705eec295d8edc77a9c741d8ce4e056b3bca00b6</td>
  </tr>
  <tr id="razorgmmb29k">
    <td>6.0.1 (MMB29K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mmb29k-factory-6cb8af22.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MMB29K]">Link</a></td>
    <td>6cb8af22ab0e42f33fa74366d57987f4e84949f8700c32cfa0e19b8431073956</td>
  </tr>
  <tr id="razorgmmb29o">
    <td>6.0.1 (MMB29O)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mmb29o-factory-eae67311.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MMB29O]">Link</a></td>
    <td>eae673113adc18432111bbb3e28ccbc8d8de63dd584906cf814cfc0dc9dc860a</td>
  </tr>
  <tr id="razorgmmb29q">
    <td>6.0.1 (MMB29Q)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mmb29q-factory-167e1d08.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MMB29Q]">Link</a></td>
    <td>167e1d08d587492e6fb80b8e9f0b4f7045e8e10dd0cd0f031adf76328d9d927f</td>
  </tr>
  <tr id="razorgmmb29v">
    <td>6.0.1 (MMB29V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mmb29v-factory-f3e59c6e.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MMB29V]">Link</a></td>
    <td>f3e59c6ee78d6e2a6bd14ffa8b6b9fc0a9fc47b3d52558f6f4520e2d8127b543</td>
  </tr>
  <tr id="razorgmmb29x">
    <td>6.0.1 (MMB29X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mmb29x-factory-ae0af307.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MMB29X]">Link</a></td>
    <td>ae0af3077a350f6e5b4e8b44089909b288cc6fd6129e5024164ff3627d201cbb</td>
  </tr>
  <tr id="razorgmob30d">
    <td>6.0.1 (MOB30D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mob30d-factory-49fcc079.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MOB30D]">Link</a></td>
    <td>49fcc07944e8602afb975b96e9a1f92657d084b01856f8202379871c9c816695</td>
  </tr>
  <tr id="razorgmmb30h">
    <td>6.0.1 (MMB30H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mmb30h-factory-fa562bcf.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MMB30H]">Link</a></td>
    <td>fa562bcf201ee6c745151af8c12d21aea56b6995427136b7475d5edcffb3df71</td>
  </tr>
  <tr id="razorgmob30j">
    <td>6.0.1 (MOB30J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mob30j-factory-d191030c.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MOB30J]">Link</a></td>
    <td>d191030cab8aed8cc3af16f5e6d4d8abb8c1151d54155bb9409e6f982474cbcd</td>
  </tr>
  <tr id="razorgmmb30j">
    <td>6.0.1 (MMB30J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mmb30j-factory-38dd789f.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MMB30J]">Link</a></td>
    <td>38dd789f2827beabc3200c7ca5f2e4bc2c0d4e023c068924b13bedc1cdbfd790</td>
  </tr>
  <tr id="razorgmob30m">
    <td>6.0.1 (MOB30M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mob30m-factory-4cd6548f.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MOB30M]">Link</a></td>
    <td>4cd6548fff3c6440b2e903f50209bfc1510f2ef91d9214e336534825df0c64c0</td>
  </tr>
  <tr id="razorgmmb30m">
    <td>6.0.1 (MMB30M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mmb30m-factory-e6005833.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MMB30M]">Link</a></td>
    <td>e600583325a4d50dce17c3aa9f3f7c7a875344d65b3b1a6e26e3f2dfdecb18a2</td>
  </tr>
  <tr id="razorgmob30p">
    <td>6.0.1 (MOB30P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mob30p-factory-4bece435.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MOB30P]">Link</a></td>
    <td>4bece43545381a49428d96708de0933c755b3433c45d79eb363fbca9da59a1d9</td>
  </tr>
  <tr id="razorgmmb30s">
    <td>6.0.1 (MMB30S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mmb30s-factory-091a2b26.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MMB30S]">Link</a></td>
    <td>091a2b263e7f71ecab03d7bed5c58333bdab16fb0856464ac78f573b7bea14df</td>
  </tr>
  <tr id="razorgmob30x">
    <td>6.0.1 (MOB30X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/razorg-mob30x-factory-10b7ca08.zip" class="gc-analytics-event" data-category="Android Images" data-label="razorg for Nexus 7 [2013] (Mobile) [MOB30X]">Link</a></td>
    <td>10b7ca083e4c0ce193904faca8841594f680e61b63da7ec38bf1e970f7375f04</td>
  </tr>
</tbody></table></div>

<h2 id="mantaray" is-upgraded="">"mantaray" for Nexus 10</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="mantarayjdq39">
    <td>4.2.2 (JDQ39)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-jdq39-factory-f36846bb.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [JDQ39]">Link</a></td>
    <td>f36846bb4b228d01d208a99b6c02f5f2f6cf9e8034510253eedf5b45acbd047a</td>
  </tr>
  <tr id="mantarayjwr66y">
    <td>4.3 (JWR66Y)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-jwr66y-factory-af9fdf29.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [JWR66Y]">Link</a></td>
    <td>af9fdf296e084ba904bcc0849746d15f3864a6524676a5cae097767f07607927</td>
  </tr>
  <tr id="mantaraykrt16s">
    <td>4.4 (KRT16S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-krt16s-factory-ffbec876.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [KRT16S]">Link</a></td>
    <td>ffbec876b1b687833ac386b3b2c97d8a2b5d02deec95f17ba98fe6492d6c77be</td>
  </tr>
  <tr id="mantaraykot49h">
    <td>4.4.2 (KOT49H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-kot49h-factory-31e93f8d.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [KOT49H]">Link</a></td>
    <td>31e93f8d2f09408ae5981a38db83705e8181f79a749de30b6249cce7d5d07327</td>
  </tr>
  <tr id="mantarayktu84l">
    <td>4.4.3 (KTU84L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-ktu84l-factory-da64399f.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [KTU84L]">Link</a></td>
    <td>da64399fd39a24232cec93b89427248df0845f9f41867f5f03cb3b0032389e22</td>
  </tr>
  <tr id="mantarayktu84p">
    <td>4.4.4 (KTU84P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-ktu84p-factory-21949d5d.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [KTU84P]">Link</a></td>
    <td>21949d5d54356388c4b97493817a40f6b3aa82d423e20d6ec119d3f8220d599d</td>
  </tr>
  <tr id="mantaraylrx21p">
    <td>5.0 (LRX21P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lrx21p-factory-0ba5bf74.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LRX21P]">Link</a></td>
    <td>0ba5bf74c2999280f06cdf7e8e61b07c43dd5b0e21cbdb18bd306125c88c5e1c</td>
  </tr>
  <tr id="mantaraylrx22c">
    <td>5.0.1 (LRX22C)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lrx22c-factory-ac6bdf60.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LRX22C]">Link</a></td>
    <td>ac6bdf60e1db208fbaf34c0adc214a9857c67db28a0ba0ad2e49ead0b9f7781d</td>
  </tr>
  <tr id="mantaraylrx22g">
    <td>5.0.2 (LRX22G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lrx22g-factory-7f1af28e.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LRX22G]">Link</a></td>
    <td>7f1af28ea70841e1bc602187cc7ee3f5531aa90e730d5a637c004c884692db5f</td>
  </tr>
  <tr id="mantaraylmy47d">
    <td>5.1.0 (LMY47D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy47d-factory-00f8e48a.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY47D]">Link</a></td>
    <td>00f8e48aae783941d7f41254d887c444402f0d624b69bd9fd0075f13980eb7a3</td>
  </tr>
  <tr id="mantaraylmy47v">
    <td>5.1.1 (LMY47V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy47v-factory-66a84c65.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY47V]">Link</a></td>
    <td>66a84c659286a9ea44a192e125bdd202d48573fcbf85cfc07a6ad24954bf42c2</td>
  </tr>
  <tr id="mantaraylmy48i">
    <td>5.1.1 (LMY48I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy48i-factory-0fa0cdbc.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY48I]">Link</a></td>
    <td>0fa0cdbc470db4a0379596c68e1579da3eb607a38aa152a4066750b43031f497</td>
  </tr>
  <tr id="mantaraylmy48m">
    <td>5.1.1 (LMY48M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy48m-factory-7fefa227.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY48M]">Link</a></td>
    <td>7fefa227f288d54814d2ce15740cb51f5fe887b4b1fe82a727b07ef584adfd24</td>
  </tr>
  <tr id="mantaraylmy48t">
    <td>5.1.1 (LMY48T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy48t-factory-6393672b.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY48T]">Link</a></td>
    <td>6393672b4dd1f2f97a3e5788efcfdb6a5730c6968b06f158351e765fa83f1495</td>
  </tr>
  <tr id="mantaraylmy48x">
    <td>5.1.1 (LMY48X)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy48x-factory-f16fd70b.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY48X]">Link</a></td>
    <td>f16fd70b3b93c47d2c73e3cbc813d8f9f7e64426ba1651837c758188c89fe8bf</td>
  </tr>
  <tr id="mantaraylmy48z">
    <td>5.1.1 (LMY48Z)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy48z-factory-335473d6.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY48Z]">Link</a></td>
    <td>335473d6a8bd4e908384c7d95994c205a8ed37ce5308992f1ef7a7e1775b625a</td>
  </tr>
  <tr id="mantaraylmy49f">
    <td>5.1.1 (LMY49F)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy49f-factory-c079e4a5.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY49F]">Link</a></td>
    <td>c079e4a5933798325e6dad6ca596ace2df9eff3c1b06fe37d82970029133459e</td>
  </tr>
  <tr id="mantaraylmy49g">
    <td>5.1.1 (LMY49G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy49g-factory-d68cbae5.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY49G]">Link</a></td>
    <td>d68cbae5f3dd41325a7112f913ac5d8e18364b740527dd2269a702d8ddd42799</td>
  </tr>
  <tr id="mantaraylmy49h">
    <td>5.1.1 (LMY49H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy49h-factory-ee7b7ce5.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY49H]">Link</a></td>
    <td>ee7b7ce5e953227990a30aee0df47ec56ca175c0e4375447aaa3215701320332</td>
  </tr>
  <tr id="mantaraylmy49j">
    <td>5.1.1 (LMY49J)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mantaray-lmy49j-factory-b24f40e6.zip" class="gc-analytics-event" data-category="Android Images" data-label="mantaray for Nexus 10 [LMY49J]">Link</a></td>
    <td>b24f40e64a1c7e4a986be9596223737fb2fe0fb739160576cc2fc1250fa85a59</td>
  </tr>
</tbody></table></div>

<h2 id="occam" is-upgraded="">"occam" for Nexus 4</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="occamjdq39">
    <td>4.2.2 (JDQ39)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-jdq39-factory-5880aa93.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [JDQ39]">Link</a></td>
    <td>5880aa93a1b14397b8162d4c4936267b52cac94035bc53db062498ecf0abf9e4</td>
  </tr>
  <tr id="occamjwr66y">
    <td>4.3 (JWR66Y)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-jwr66y-factory-2b869d2f.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [JWR66Y]">Link</a></td>
    <td>2b869d2f61c53a6018b48d13dfb3078bbd87ac79bba3339f1259c9dad1a23952</td>
  </tr>
  <tr id="occamkrt16s">
    <td>4.4 (KRT16S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-krt16s-factory-3fb36835.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [KRT16S]">Link</a></td>
    <td>3fb36835bf216b0d1426db5455ba7c435535b31b28dc1b9a16f77406f1b0c4ce</td>
  </tr>
  <tr id="occamkot49h">
    <td>4.4.2 (KOT49H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-kot49h-factory-e859c810.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [KOT49H]">Link</a></td>
    <td>e859c810cb053b55e95e9663a33fe0175b5a388435d5d0850be58194bbb7d4e5</td>
  </tr>
  <tr id="occamktu84l">
    <td>4.4.3 (KTU84L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-ktu84l-factory-6e75c072.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [KTU84L]">Link</a></td>
    <td>6e75c072c9f4ece87e1bc4094b397bf86f4baf9b2141effd44ac13a4d2e1625f</td>
  </tr>
  <tr id="occamktu84p">
    <td>4.4.4 (KTU84P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-ktu84p-factory-2373a541.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [KTU84P]">Link</a></td>
    <td>2373a5419f8e1f35f05f916d9ad2979b106b03193c3906e41c3e6d215d6d5076</td>
  </tr>
  <tr id="occamlrx21t">
    <td>5.0 (LRX21T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-lrx21t-factory-96341e4d.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [LRX21T]">Link</a></td>
    <td>96341e4d26586141f404a293345d0fc0483b4a9b5654ebdd07dd987340cf44f9</td>
  </tr>
  <tr id="occamlrx22c">
    <td>5.0.1 (LRX22C)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-lrx22c-factory-3657b013.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [LRX22C]">Link</a></td>
    <td>3657b013b097a893d5a84bcdb43093ba463f44abc7926879a31926986a3941d9</td>
  </tr>
  <tr id="occamlmy47o">
    <td>5.1.0 (LMY47O)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-lmy47o-factory-41497579.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [LMY47O]">Link</a></td>
    <td>414975799076d8f6997d2b028e84c9dd5ac9eb45ca44106dc059b7b86989d236</td>
  </tr>
  <tr id="occamlmy47v">
    <td>5.1.1 (LMY47V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-lmy47v-factory-85f8c9ff.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [LMY47V]">Link</a></td>
    <td>85f8c9ff82f2eb60abacc9abacac19b3a837c044a974bc2b00874feff38f2567</td>
  </tr>
  <tr id="occamlmy48i">
    <td>5.1.1 (LMY48I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-lmy48i-factory-f0ac517a.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [LMY48I]">Link</a></td>
    <td>f0ac517ad0ff8261fae610bec4e9f145d99a078fe066e406e6951ce4c21fd1bd</td>
  </tr>
  <tr id="occamlmy48m">
    <td>5.1.1 (LMY48M)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-lmy48m-factory-791d6c4a.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [LMY48M]">Link</a></td>
    <td>791d6c4a716ceadbb830d67db823f377067becd2eca6dae5a00b38f5b1ddcb26</td>
  </tr>
  <tr id="occamlmy48t">
    <td>5.1.1 (LMY48T)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/occam-lmy48t-factory-c43c7cfd.zip" class="gc-analytics-event" data-category="Android Images" data-label="occam for Nexus 4 [LMY48T]">Link</a></td>
    <td>c43c7cfd7e77ae97dad0c2e0f3810f84bc5e2ca3b4dc74256eb7e13012ec1131</td>
  </tr>
</tbody></table></div>

<h2 id="nakasi" is-upgraded="">"nakasi" for Nexus 7 (Wi-Fi)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="nakasijzo54k">
    <td>4.1.2 (JZO54K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-jzo54k-factory-25cab35c.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [JZO54K]">Link</a></td>
    <td>25cab35cfc81a7d92679deece485590dd62070882124149295ded95463a1eb4f</td>
  </tr>
  <tr id="nakasijdq39">
    <td>4.2.2 (JDQ39)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-jdq39-factory-1ed5719b.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [JDQ39]">Link</a></td>
    <td>1ed5719bbf2a709f090f8d1da5c3afc62d6fcb381ee2559f130639873e1d7283</td>
  </tr>
  <tr id="nakasijwr66y">
    <td>4.3 (JWR66Y)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-jwr66y-factory-201de0b2.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [JWR66Y]">Link</a></td>
    <td>201de0b22cac0d5c8d51b249bf85dbe803b9a63b3eb1a7ceea0a4379b81b132c</td>
  </tr>
  <tr id="nakasikrt16s">
    <td>4.4 (KRT16S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-krt16s-factory-7e5a4463.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [KRT16S]">Link</a></td>
    <td>7e5a44631d7f7df7312c52fedd5fdd5ec4a2d94a99d173c8e67865bb267b6cba</td>
  </tr>
  <tr id="nakasikot49h">
    <td>4.4.2 (KOT49H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-kot49h-factory-f0e49b7a.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [KOT49H]">Link</a></td>
    <td>f0e49b7a6a4bbe82019a60b919a75c9c18425c869e5de95c8b78fe13c2e00795</td>
  </tr>
  <tr id="nakasiktu84l">
    <td>4.4.3 (KTU84L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-ktu84l-factory-93385880.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [KTU84L]">Link</a></td>
    <td>933858800b0fa94d2ee2289506c10065e2be9570852d845fa1732925031e380a</td>
  </tr>
  <tr id="nakasiktu84p">
    <td>4.4.4 (KTU84P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-ktu84p-factory-9482e892.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [KTU84P]">Link</a></td>
    <td>9482e892e274e27cc18028e82e206b2e9de82f17cd29ea6ab526592e997112d9</td>
  </tr>
  <tr id="nakasilrx21p">
    <td>5.0 (LRX21P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-lrx21p-factory-7d66743e.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [LRX21P]">Link</a></td>
    <td>7d66743ed60fba0d83a44513c7a98e912302fa5c1f5634c33a38a08510f82885</td>
  </tr>
  <tr id="nakasilrx22g">
    <td>5.0.2 (LRX22G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-lrx22g-factory-386f8be2.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [LRX22G]">Link</a></td>
    <td>386f8be2ae4ca68486535130f19eae68c93c59c770ea3e1e2da7b1876a15dd40</td>
  </tr>
  <tr id="nakasilmy47d">
    <td>5.1.0 (LMY47D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-lmy47d-factory-7f853a00.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [LMY47D]">Link</a></td>
    <td>7f853a00ac20643c216e28f220a34c14024404240c9dd5f6002de4f982be8c2c</td>
  </tr>
  <tr id="nakasilmy47v">
    <td>5.1.1 (LMY47V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasi-lmy47v-factory-5a0bb059.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasi for Nexus 7 (Wi-Fi) [LMY47V]">Link</a></td>
    <td>5a0bb0593ee9867bee61d59e94462e681c050da9db1397db98616e8887034614</td>
  </tr>
</tbody></table></div>

<h2 id="nakasig" is-upgraded="">"nakasig" for Nexus 7 (Mobile)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="nakasigjdq39">
    <td>4.2.2 (JDQ39)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasig-jdq39-factory-3ec66003.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasig for Nexus 7 (Mobile) [JDQ39]">Link</a></td>
    <td>3ec660030b502a34bb2ed037eff55c79545b9b11f0bcf5f4b66c23647d029a83</td>
  </tr>
  <tr id="nakasigjwr66y">
    <td>4.3 (JWR66Y)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasig-jwr66y-factory-cd7ba7a0.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasig for Nexus 7 (Mobile) [JWR66Y]">Link</a></td>
    <td>cd7ba7a0af525ba276442ad6d061f1cdb1a00daba8165fb28d6b4eb887c26184</td>
  </tr>
  <tr id="nakasigkrt16s">
    <td>4.4 (KRT16S)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasig-krt16s-factory-e2560231.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasig for Nexus 7 (Mobile) [KRT16S]">Link</a></td>
    <td>e25602316aa198ac6afddb40c5758749b5b47e4574b3289fa07c6a7f063c9002</td>
  </tr>
  <tr id="nakasigkot49h">
    <td>4.4.2 (KOT49H)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasig-kot49h-factory-62469636.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasig for Nexus 7 (Mobile) [KOT49H]">Link</a></td>
    <td>624696368457946bce4b34a42759ab35ba1e226ffbfde5316118ec0a5f42ee51</td>
  </tr>
  <tr id="nakasigktu84l">
    <td>4.4.3 (KTU84L)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasig-ktu84l-factory-d2e16b2a.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasig for Nexus 7 (Mobile) [KTU84L]">Link</a></td>
    <td>d2e16b2a7c81d1f6cea2a60f61cfa983cf181cdbb6224b41cfb3bb4e32bcd386</td>
  </tr>
  <tr id="nakasigktu84p">
    <td>4.4.4 (KTU84P)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasig-ktu84p-factory-ddaf3885.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasig for Nexus 7 (Mobile) [KTU84P]">Link</a></td>
    <td>ddaf388582775b569539a43791f94cb6b3475559864ee438e7e6a8b492406f86</td>
  </tr>
  <tr id="nakasiglrx22g">
    <td>5.0.2 (LRX22G)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasig-lrx22g-factory-bbbc5d72.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasig for Nexus 7 (Mobile) [LRX22G]">Link</a></td>
    <td>bbbc5d726de1af4c524830a39de4431c17531b4affab3bc2d81375a4d914abfb</td>
  </tr>
  <tr id="nakasiglmy47d">
    <td>5.1.0 (LMY47D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasig-lmy47d-factory-3cccf586.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasig for Nexus 7 (Mobile) [LMY47D]">Link</a></td>
    <td>3cccf586cea8a8117e6577d73f41d093e7450d33157e870195cd50ca9c458285</td>
  </tr>
  <tr id="nakasiglmy47v">
    <td>5.1.1 (LMY47V)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/nakasig-lmy47v-factory-f96fcd16.zip" class="gc-analytics-event" data-category="Android Images" data-label="nakasig for Nexus 7 (Mobile) [LMY47V]">Link</a></td>
    <td>f96fcd164f2ef8f1d7c88efd553b6b7193fe56326e5ad4829a6f9eeb961c66cf</td>
  </tr>
</tbody></table></div>

<h2 id="tungsten" is-upgraded="">"tungsten" for Nexus Q</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="tungstenian67k">
    <td>4.0.4 (IAN67K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/tungsten-ian67k-factory-d766e5f1.zip" class="gc-analytics-event" data-category="Android Images" data-label="tungsten for Nexus Q [IAN67K]">Link</a></td>
    <td>d766e5f1eb7cd276864bb255593279788a4c44a3935907ec3b5b0bc859e21c2d</td>
  </tr>
</tbody></table></div>

<h2 id="takju" is-upgraded="">"takju" for Galaxy Nexus "maguro" (GSM/HSPA+) (with Google Wallet)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="takjuimm76i">
    <td>4.0.4 (IMM76I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/takju-imm76i-factory-1c4370b4.zip" class="gc-analytics-event" data-category="Android Images" data-label="takju for Galaxy Nexus maguro (GSM/HSPA+) (with Google Wallet) [IMM76I]">Link</a></td>
    <td>1c4370b411bd23179277e8bc42f1eb8c9a344980bf30e30577b2f6f018249212</td>
  </tr>
  <tr id="takjujzo54k">
    <td>4.1.2 (JZO54K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/takju-jzo54k-factory-50c467ac.zip" class="gc-analytics-event" data-category="Android Images" data-label="takju for Galaxy Nexus maguro (GSM/HSPA+) (with Google Wallet) [JZO54K]">Link</a></td>
    <td>50c467acdc6e7d512663ac587207a0b1eadb762e5d66afbc004d3081ee833bc4</td>
  </tr>
  <tr id="takjujdq39">
    <td>4.2.2 (JDQ39)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/takju-jdq39-factory-4bf9521a.zip" class="gc-analytics-event" data-category="Android Images" data-label="takju for Galaxy Nexus maguro (GSM/HSPA+) (with Google Wallet) [JDQ39]">Link</a></td>
    <td>4bf9521a436e3d1db194a5e1837729088a4a5ad1e57ea09b1c59afdef2868a04</td>
  </tr>
  <tr id="takjujwr66y">
    <td>4.3 (JWR66Y)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/takju-jwr66y-factory-c042afa0.zip" class="gc-analytics-event" data-category="Android Images" data-label="takju for Galaxy Nexus maguro (GSM/HSPA+) (with Google Wallet) [JWR66Y]">Link</a></td>
    <td>c042afa00fbfaf547ff767dfa9f72df1421525c1e3dbc77fa58dc69aaa423355</td>
  </tr>
</tbody></table></div>

<h2 id="yakju" is-upgraded="">"yakju" for Galaxy Nexus "maguro" (GSM/HSPA+)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="yakjuimm76i">
    <td>4.0.4 (IMM76I)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/yakju-imm76i-factory-7e04639e.zip" class="gc-analytics-event" data-category="Android Images" data-label="yakju for Galaxy Nexus maguro (GSM/HSPA+) [IMM76I]">Link</a></td>
    <td>7e04639eee9459a94ee4ae7d1675e5a857bbf89ce36f4140db8dc68e4b00c3fa</td>
  </tr>
  <tr id="yakjujzo54k">
    <td>4.1.2 (JZO54K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/yakju-jzo54k-factory-d75228cf.zip" class="gc-analytics-event" data-category="Android Images" data-label="yakju for Galaxy Nexus maguro (GSM/HSPA+) [JZO54K]">Link</a></td>
    <td>d75228cffdc9d0f88d6ed9c63f79c35123269a1ed860df305fcbb00f03b438b6</td>
  </tr>
  <tr id="yakjujdq39">
    <td>4.2.2 (JDQ39)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/yakju-jdq39-factory-6f07b069.zip" class="gc-analytics-event" data-category="Android Images" data-label="yakju for Galaxy Nexus maguro (GSM/HSPA+) [JDQ39]">Link</a></td>
    <td>6f07b0690a3853fb7bd9915be2ea38525486c9fa0c474daca70de713c9671485</td>
  </tr>
  <tr id="yakjujwr66y">
    <td>4.3 (JWR66Y)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/yakju-jwr66y-factory-4cadea65.zip" class="gc-analytics-event" data-category="Android Images" data-label="yakju for Galaxy Nexus maguro (GSM/HSPA+) [JWR66Y]">Link</a></td>
    <td>4cadea65393c1cc6f2a61232001fc34a37d4a8c95c2439ada3573682a18b139c</td>
  </tr>
</tbody></table></div>

<h2 id="mysid" is-upgraded="">"mysid" for Galaxy Nexus "toro" (Verizon CDMA/LTE)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="mysidimm76k">
    <td>4.0.4 (IMM76K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mysid-imm76k-factory-09d74d64.zip" class="gc-analytics-event" data-category="Android Images" data-label="mysid for Galaxy Nexus toro (Verizon CDMA/LTE) [IMM76K]">Link</a></td>
    <td>09d74d643fd37411efeb66050883de389142788c8eccbd36360dd5c0127babb7</td>
  </tr>
  <tr id="mysidjro03o">
    <td>4.1.1 (JRO03O)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mysid-jro03o-factory-1cc98d31.zip" class="gc-analytics-event" data-category="Android Images" data-label="mysid for Galaxy Nexus toro (Verizon CDMA/LTE) [JRO03O]">Link</a></td>
    <td>1cc98d314f94cc873853831936d00f9cab9be774f8b78fc5fd0d791e79e4bdaa</td>
  </tr>
  <tr id="mysidjdq39">
    <td>4.2.2 (JDQ39)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mysid-jdq39-factory-335d5931.zip" class="gc-analytics-event" data-category="Android Images" data-label="mysid for Galaxy Nexus toro (Verizon CDMA/LTE) [JDQ39]">Link</a></td>
    <td>335d5931c3860e37748e26d719e9d18e5baf9e9f0bd2af9ad716113caac1d1c7</td>
  </tr>
</tbody></table></div>

<h2 id="mysidspr" is-upgraded="">"mysidspr" for Galaxy Nexus "toroplus" (Sprint CDMA/LTE)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="mysidsprfh05">
    <td>4.1.1 (FH05)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mysidspr-fh05-factory-ff03148b.zip" class="gc-analytics-event" data-category="Android Images" data-label="mysidspr for Galaxy Nexus toroplus (Sprint CDMA/LTE) [FH05]">Link</a></td>
    <td>ff03148b27757fb7e83dc6a545f51ddc8b808e612406cf92b2f0516104cb8bc5</td>
  </tr>
  <tr id="mysidsprga02">
    <td>4.2.1 (GA02)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/mysidspr-ga02-factory-063123bd.zip" class="gc-analytics-event" data-category="Android Images" data-label="mysidspr for Galaxy Nexus toroplus (Sprint CDMA/LTE) [GA02]">Link</a></td>
    <td>063123bd699b1dfaef38591ad44bba453df1765051e7eedbc0ab5adba35fa04b</td>
  </tr>
</tbody></table></div>

<h2 id="soju" is-upgraded="">"soju" for Nexus S (worldwide version, i9020t and i9023)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="sojugrk39f">
    <td>2.3.6 (GRK39F)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/soju-grk39f-factory-8e283784.zip" class="gc-analytics-event" data-category="Android Images" data-label="soju for Nexus S (worldwide version, i9020t and i9023) [GRK39F]">Link</a></td>
    <td>8e2837843881e0848d8307f01eaefb1489762e6eeda36f62812447277d0eb638</td>
  </tr>
  <tr id="sojuimm76d">
    <td>4.0.4 (IMM76D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/soju-imm76d-factory-c6e0efe3.zip" class="gc-analytics-event" data-category="Android Images" data-label="soju for Nexus S (worldwide version, i9020t and i9023) [IMM76D]">Link</a></td>
    <td>c6e0efe396c9e1bc9f932926b4c439fecc56f624c6c9bee920d7410ead23f243</td>
  </tr>
  <tr id="sojujzo54k">
    <td>4.1.2 (JZO54K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/soju-jzo54k-factory-3534fc3e.zip" class="gc-analytics-event" data-category="Android Images" data-label="soju for Nexus S (worldwide version, i9020t and i9023) [JZO54K]">Link</a></td>
    <td>3534fc3ecd8d9742791f18d6e427ba342db6adacbfbe3c5f1f6bfcc5da0cbbd8</td>
  </tr>
</tbody></table></div>

<h2 id="sojua" is-upgraded="">"sojua" for Nexus S (850MHz version, i9020a)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="sojuagrk39f">
    <td>2.3.6 (GRK39F)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sojua-grk39f-factory-cad4ab8a.zip" class="gc-analytics-event" data-category="Android Images" data-label="sojua for Nexus S (850MHz version, i9020a) [GRK39F]">Link</a></td>
    <td>cad4ab8aab10b37467795b0e7ddde6d63360ed9c6f27a2034d66ca5938877acd</td>
  </tr>
  <tr id="sojuaimm76d">
    <td>4.0.4 (IMM76D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sojua-imm76d-factory-174c6bd1.zip" class="gc-analytics-event" data-category="Android Images" data-label="sojua for Nexus S (850MHz version, i9020a) [IMM76D]">Link</a></td>
    <td>174c6bd19aa4e0d56187f64d09bdc595e601a4f48c048630acce443a692f4b97</td>
  </tr>
  <tr id="sojuajzo54k">
    <td>4.1.2 (JZO54K)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sojua-jzo54k-factory-860d0729.zip" class="gc-analytics-event" data-category="Android Images" data-label="sojua for Nexus S (850MHz version, i9020a) [JZO54K]">Link</a></td>
    <td>860d072998c6a5764a5c3b7d3a2c266615959751d550077170b45f8851bcaf6f</td>
  </tr>
</tbody></table></div>

<h2 id="sojuk" is-upgraded="">"sojuk" for Nexus S (Korea version, m200)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="sojukgrk39f">
    <td>2.3.6 (GRK39F)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sojuk-grk39f-factory-3910e795.zip" class="gc-analytics-event" data-category="Android Images" data-label="sojuk for Nexus S (Korea version, m200) [GRK39F]">Link</a></td>
    <td>3910e795e66e3e5beb74e6246ac1b59280a2abaea3d99b83dee70ea32d0ec2eb</td>
  </tr>
  <tr id="sojukimm76d">
    <td>4.0.4 (IMM76D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sojuk-imm76d-factory-9a5468c1.zip" class="gc-analytics-event" data-category="Android Images" data-label="sojuk for Nexus S (Korea version, m200) [IMM76D]">Link</a></td>
    <td>9a5468c1aeaa201bf42553b86e6bbf83eefd237e540c13c9f783fa4aed3ae9e3</td>
  </tr>
  <tr id="sojukjro03e">
    <td>4.1.1 (JRO03E)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sojuk-jro03e-factory-176dca0a.zip" class="gc-analytics-event" data-category="Android Images" data-label="sojuk for Nexus S (Korea version, m200) [JRO03E]">Link</a></td>
    <td>176dca0aacb4601ed67961a4ab3b32714a93ec608adf3f4e1e287beebbeb4403</td>
  </tr>
</tbody></table></div>

<h2 id="sojus" is-upgraded="">"sojus" for Nexus S 4G (d720)</h2>

<div class="devsite-table-wrapper"><table>
  <thead>
    <tr><th>Version</th>
    <th>Download</th>
    <th>SHA-256 Checksum</th>
  </tr></thead>
  <tbody><tr id="sojusgwk74">
    <td>2.3.7 (GWK74)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sojus-gwk74-factory-fe1fe884.zip" class="gc-analytics-event" data-category="Android Images" data-label="sojus for Nexus S 4G (d720) [GWK74]">Link</a></td>
    <td>fe1fe8846d8b8e3642a5b303cb20b9aefd6e46e9f5ad142a754178eb5c937f76</td>
  </tr>
  <tr id="sojusimm76d">
    <td>4.0.4 (IMM76D)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sojus-imm76d-factory-e4190dff.zip" class="gc-analytics-event" data-category="Android Images" data-label="sojus for Nexus S 4G (d720) [IMM76D]">Link</a></td>
    <td>e4190dff02df6cda7c4109c76ccf758071ab03f87d48720c9d36e7f817fb3d92</td>
  </tr>
  <tr id="sojusjro03r">
    <td>4.1.1 (JRO03R)</td>
    <td><a href="https://dl.google.com/dl/android/aosp/sojus-jro03r-factory-b7868911.zip" class="gc-analytics-event" data-category="Android Images" data-label="sojus for Nexus S 4G (d720) [JRO03R]">Link</a></td>
    <td>b78689114651587d1ff34ab4d3af9dc0885da3c6f70807e47c6dbdf634385f2a</td>
  </tr>
</tbody></table></div>
