---
title: Accessing Android Data Directory
aliases:
- /Accessing_Android_Data_Directory
---

# Accessing Android Data Directory
Starting with Luanti 5.4.2, the Android version now stores its user data in its scoped app storage at `/storage/emulated/0/Android/data/net.minetest.minetest/files/Minetest`. This is caused by a restriction of recent Android API levels and Google Play policies and it is unfortunately impossible to store it in the old more accessible `/storage/emulated/0/Minetest/` location.

While it is officially intended by Google to not be accessible to regular users, there are still ways to circumvent it and still access the folder.

## Total Commander workaround (Android <=12)
[Total Commander](https://play.google.com/store/apps/details?id=com.ghisler.android.TotalCommander) (and possibly other file managers) has a method to workaround the restrictions put in place by Google, by taking advantage of a bug in Android 12 and below* that allows file managers to be given permission to `Android/data/`.

\* Some vendor ROMs based on Android 13 and above may still have this bug present, while phones closely based on stock Android likely have it fixed.

Navigate to `Internal shared storage > Android > data`. Press on the folder named `-> Installed apps`.

![](/images/accessing_android_data/tc_1.webp)

It will prompt you to grant Total Commander access to this folder. Simply press "Yes".

![](/images/accessing_android_data/tc_2.webp)

It will take you to a screen that looks something like this. **Do not navigate into the Luanti folder or any other one**, simply press the "Use this folder" button at the bottom.

![](/images/accessing_android_data/tc_3.webp)

If you get a confirmation prompt, just press the allow button.

![](/images/accessing_android_data/tc_4.webp)

You should be brought to the `/Android/data` directory listing in Total Commander now. Find the `net.minetest.minetest` folder and go inside the `files` folder and then the `Minetest` folder, which is where the engine's user data files now reside.

For instructions on how to create a bookmark shortcut to the folder, see [this forum thread](https://forum.luanti.org/viewtopic.php?f=18&t=27684).

## Through ADB (Needs computer)
You can access the scoped storage through ADB, a debugging tool part of the [Android platform tools](https://developer.android.com/studio/releases/platform-tools). In order to use ADB, you will need to enable USB debugging from the Android developer settings and connect your phone to a computer. On Linux, it should work out of the box. However on Windows you will need to find so called "ADB drivers" from your phone's manufacturer.

ADB is primarily a command-line tool, and you usually would want to use the `adb pull` and `adb push` commands similar to working with something like SCP. ADB also supports tab autocompletion on the remote side, so you can look at the directory structure on your phone while typing out a command. Some example commands:

* **Pushing a world from your computer onto your phone:** `adb push cool_world/ /storage/emulated/0/Android/data/net.minetest.minetest/files/Minetest/worlds/`

* **Manually installing a mod not available on ContentDB:** `adb push indev_mod/ /storage/emulated/0/Android/data/net.minetest.minetest/files/Minetest/mods/`

* **Backing up a world to your computer:** `adb pull /storage/emulated/0/Android/data/net.minetest.minetest/files/Minetest/worlds/cool_world/ cool_world_android_backup/`

* **Backing up your entire Android user data to your computer:** `adb pull /storage/emulated/0/Android/data/net.minetest.minetest/files/Minetest/ minetest_android_backup/`

The `adb shell` command is also available allowing you to launch a shell on your phone, use `cd /storage/emulated/0/Android/data/net.minetest.minetest/files/Minetest` to navigate into the user data and manage it with regular Linux terminal commands.
