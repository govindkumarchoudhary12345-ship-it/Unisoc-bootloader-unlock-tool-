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

## 🚀 Step 2: All Termux & Fastboot Unlock Commands

Connect the OTG adapter to your Host phone and plug the USB cable into the target phone (in Fastboot mode). Then run the commands below:

```bash
# 1. Update packages & install dependencies
pkg update && pkg upgrade -y
pkg install android-tools python git openssl libusb -y

# 2. Install Unisoc unlock utility
pip install unisoc-unlock

# 3. Check fastboot connection
fastboot devices

# 4. Method A: Direct Fastboot Unlock
fastboot flashing unlock

# 5. Method B: Automated Unisoc Unlock Utility (if direct unlock fails)
python -m unisoc_unlock unlock

# 6. Method C: Get Device Identifier Token Manually (Optional)
fastboot oem get_identifier_token
