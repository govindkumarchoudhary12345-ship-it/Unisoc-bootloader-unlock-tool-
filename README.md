# Unisoc Bootloader Unlock (No PC - Termux Method)

Unlock the bootloader for Unisoc (Spreadtrum) smartphones like **POCO C71** (and similar models like Redmi A-series) without a PC, using another Android phone via Termux and USB-OTG.

---

## ⚠️ Disclaimer
Unlocking the bootloader will **wipe all internal data** (Factory Reset). Please back up your device before starting. Carrier-locked variants (such as Airtel Prepaid Locked) cannot be unlocked via standard fastboot commands.

---

## 📋 Requirements
- **Host Device:** Any working Android phone with Termux installed.
- **Target Device:** Your Unisoc phone (POCO C71) with at least 50% battery.
- **Hardware:** USB OTG adapter plugged into the Host Phone + USB cable to the target phone.

---

## ⚙️ Step 1: Prepare Target Phone (POCO C71)
1. Open **Settings > About Phone**.
2. Tap **Build Number** 7 times continuously until Developer Options are enabled.
3. Go to **Settings > System > Developer Options**.
4. Turn ON **OEM Unlocking**.
5. Turn ON **USB Debugging**.
6. Switch off the phone completely.
7. Press and hold **Volume Down + Power** buttons together until the screen enters **Fastboot Mode**.

---

## 📦 Step 2: Install Packages (Host Phone)

### 1. Update Packages & Dependencies
```bash
pkg update && pkg upgrade -y
pkg install android-tools python git openssl libusb -y
pip install unisoc-unlock
fastboot devices
fastboot flashing unlock
python -m unisoc_unlock unlock
fastboot oem get_identifier_token
📱 Step 5: Confirm on Phone Screen (e.g., POCO C71)
Look at your phone (like POCO C71) screen.
A confirmation warning will appear asking whether you want to unlock the bootloader.
Press the Volume Down button (or the button displayed on your screen) to select and confirm Unlock.
The device will automatically wipe all data (factory reset) and reboot with an unlocked bootloader.

