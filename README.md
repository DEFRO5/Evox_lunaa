# Flashing Instructions for Realme GT Master edition (RMX3360/61/63)

This guide provides detailed instructions for clean flashing custom ROMs on the Realme GT me(Lunaa) device.

---

## Bootloader Unlock Required

Your device must have an **unlocked bootloader**.

If your bootloader is not yet unlocked, unfortunately realme closed their servers, spam realme here:
[https://x.com/mvimal2607/status/1875859792092340641](https://x.com/mvimal2607/status/1875859792092340641)

---

## Clean Flash Recommended

A clean flash is recommended, even if you are coming from a different build of the same ROM (including builds from other developers) only do dirty flash if its particularly mentioned.

---

## Prerequisites

- Download [Android Platform Tools](https://developer.android.com/tools/releases/platform-tools).
- Place the following files in the **platform-tools** directory:
  - The ROM zip file
  - The recovery files
  - `flash.sh` (Linux) or `flash.bat` (Windows) for recovery flashing

---

## Flashing Steps (Clean Flash)

1. **Boot into Fastboot Mode**  
   Power off the device and press **Volume Down + Power** until the Fastboot screen appears.

2. **Reset data and cache via Fastboot**  
   Open a terminal or command prompt in the platform-tools folder and run:
   ```
   fastboot -w
   ```

3. **Flash the Recovery**  
   - On Linux: Run `flash.sh`  
   - On Windows: Run `flash.bat`
   
   The device will automatically reboot into recovery after flashing.

4. **Factory reset from Recovery**  
   In the recovery menu, choose:
   **Wipe data/factory reset**
   
   Note: This process will completely erase all data on the device. Ensure you have a full backup before proceeding.

5. **Sideload the ROM via ADB**  
   - On the device, select:
     **Apply update > Apply from ADB**
     
   - On your PC, in the platform-tools directory, run:
     ```
     adb sideload <rom-filename>.zip
     ```

6. **Reboot System**  
   Once sideload is complete, when prompted to flash additional modules, select **No**, then choose **Reboot system now**.

**Congratulations! You have successfully flashed the ROM.**

---

## Dirty Flash

Dirty flashing allows you to update your existing ROM without wiping user data. This is suitable when upgrading within the same ROM base.

1. **Reboot to Recovery**  
   Boot your device into recovery mode by first entering Fastboot mode and then selecting the option to reboot to recovery, or by running the following command on your PC:
   ```
   adb reboot recovery
   ```

2. **Sideload the ROM**  
   On the device, select:
   **Apply update > Apply from ADB**
   
   On your PC, in the platform-tools directory, run:
   ```
   adb sideload <rom-filename>.zip
   ```

3. **Reboot System**  
   Once sideload is complete, when prompted to flash additional modules, select **No**, then choose **Reboot system now**.

---

## Optional: Root with SUKISU

To root the ROM using SUKISU:

1. After successfully booting the ROM, reboot the device into **Fastboot mode**.

2. Extract `boot.img` from the `sukisu.zip` package.

3. Flash the boot image using:
   ```
   fastboot flash boot boot.img
   ```

4. **Reboot System**  
   Reboot the device to complete the rooting process.

---

## Disclaimer

These instructions are provided as-is. Flashing custom software carries inherent risks. Proceed only if you understand the process. The maintainer is not responsible for data loss or device damage resulting from misuse or improper flashing.
