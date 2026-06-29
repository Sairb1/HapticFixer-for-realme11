<div align="center">

# 📳 OOS15 Haptic & Fingerprint Fix

### Restore UI Touch Haptics, Gboard Vibration & Screen-Off Fingerprint Unlock on Nord 3 Port ROMs

<img width="1774" height="887" alt="oos15" src="https://github.com/user-attachments/assets/0a5420f1-18af-48e0-a877-648f319765ba" />


<a href="https://github.com/Sairb1/OOS15_Haptic_Fingerprint_Fix/releases">
  <img src="https://img.shields.io/badge/Port%20Device-Realme%20%7C%2011%205G-brightgreen?style=for-the-badge"/>
</a>
<a href="https://github.com/Sairb1/OOS_Haptic_Fingerprint_Fix/releases">
  <img src="https://img.shields.io/badge/ROM-Nord%203%20Port%20(OOS15%2F16)-blue?style=for-the-badge"/>
</a>
<a href="https://github.com/Sairb1/OOS15_Haptic_Fingerprint_Fix/releases">
  <img src="https://img.shields.io/badge/Root-Magisk%20%7C%20KernelSU%20%7C%20APatch-orange?style=for-the-badge"/>
</a>
<a href="https://github.com/Sairb1/OOS15_Haptic_Fingerprint_Fix/releases">
  <img src="https://img.shields.io/badge/Android-15%2B-red?style=for-the-badge"/>
</a>
<a href="https://t.me/colorosmodules">
  <img src="https://img.shields.io/badge/Telegram-colorosmodules-229ED9?style=for-the-badge&logo=telegram"/>
</a>

<br/>

### Premium haptic restoration & side fingerprint fix for OxygenOS 15/16 Port ROMs

Made with ♥ by **[Ayan (@imnotaino)](https://t.me/imnotaino)**  
Updates & Support → **https://t.me/colorosmodules**

</div>

---

# 📖 What is this?

**OOS15 Haptic & Fingerprint Fix** is a specialized Magisk / KernelSU / APatch module built specifically for **MT6835** devices such as the **Realme 11x 5G** and **Realme 11 5G** running **OxygenOS 15/16 (Nord 3 Port)** ROMs.

When porting a flagship ROM like the **OnePlus Nord 3** onto lower-end hardware, several hardware abstraction mismatches occur.

These mismatches break:
- UI touch vibration
- Gboard haptics
- Screen-off fingerprint unlock
- Various OPLUS feature flags

This module resolves those issues system-lessly by overriding framework feature flags, vibrator configurations and fingerprint properties before Android loads them.

---

# ⚠️ Hardware Mismatch

| Feature | Nord 3 (Port Base) | Realme 11 5G | Result |
|---------|--------------------|-----------------|--------|
| **Vibrator** | Premium Linear Motor HAL (`LMVibrator` / `RichTap`) | Standard regulator vibrator | ❌ No UI & Gboard vibration |
| **Fingerprint** | Under-display Optical Sensor | Side Capacitive Sensor | ❌ Screen-off fingerprint disabled |
| **Display** | AMOLED with native AOD | LCD (No AOD) | ❌ Screen-off lag & unnecessary battery drain |

---

# ✨ Features

## 📳 UI & Gboard Haptic Restore

Restores proper vibration by bypassing the missing **LMVibrator** implementation.

The module:

- Disables LMVibrator / RichTap framework flags
- Restores original 75KB vibration waveforms
- Injects Gboard vibration duration mapping
- Resets invalid touch intensity values
- Redirects vibration requests to the standard AIDL vibrator HAL

Result:

- ✅ System UI vibration
- ✅ Navigation haptics
- ✅ Gboard vibration
- ✅ Touch feedback

---

## 🔑 Screen-Off Fingerprint Unlock

Restores side-mounted fingerprint unlock while the display is off.

The module:

- Forces optical fingerprint support to disabled
- Removes optical fingerprint feature flags
- Enables side capacitive listener during screen-off
- Restores instant fingerprint wake

Result:

- ✅ Screen-off fingerprint unlock
- ✅ Faster unlock response
- ✅ Proper side sensor detection

---

## ⚡ Early Boot Mount

Uses **post-mount.sh** during Magisk/APatch early boot.

This guarantees:

- XML overlays are mounted before `system_server`
- Feature flags are loaded correctly
- No runtime replacement required

---

# ⚡ Premium Flashing Experience

Includes a premium flashing interface featuring:

- Animated installation progress
- Live device information
- Android version detection
- Kernel version parsing
- Battery percentage
- Automatic Telegram launcher after installation

---

# 📸 Flash Preview

```text
╔══════════════════════════════════════╗
║         OOS15 Haptic & FP Fix        ║
║      Vibration & Fingerprint Fix     ║
╚══════════════════════════════════════╝

  Developer : Ayan (@imnotaino)
  Channel   : t.me/colorosmodules

  Flash Time : 2026-06-29 11:04:35

──────────────────────────────────────
          ★ Device Info ★
──────────────────────────────────────

  Device  : realme 11 5G
  Codename: chongqind
  Android : 15 (SDK 35)
  Build   : CPH2491_15.0.0.xxx
  Kernel  : 5.15.x
  Battery : 82%

──────────────────────────────────────

  ► Initializing fix engine...
  ► Disabling LMVibrator & RichTap...
  ► Restoring stock vibration waveforms...
  ► Patching fingerprint framework...
  ► Injecting side fingerprint support...
  ► Applying runtime properties...
  ► Finalizing installation...

══════════════════════════════════════
      ✓ OOS15 Haptic & FP Fix Ready!
══════════════════════════════════════

  ➤ t.me/colorosmodules

  Made with ♥ by Ayan (@imnotaino)
```

---

# 📦 What the Module Modifies

The module overlays:

```text
/my_product/etc/permissions/oplus.feature.android.xml
/my_product/etc/permissions/oplus.product.feature_multimedia_unique.xml
/my_product/etc/permissions/oplus.product.display_features.xml
/my_product/etc/extension/com.oplus.oplus-feature.xml
/my_product/etc/vibrator/effect_waveform.xml
/my_product/etc/vibrator/effect2waveform.xml
/my_product/etc/vibrator_service_config/inputmethod_duration_map.xml
```

It also overrides the following properties during boot:

```properties
persist.vendor.fingerprint.optical.support=0
persist.sys.linearmotor.enable=0
ro.oplus.vibrator.lmvibrator=false
ro.vendor.vibrator.hal.lm=0
```

---

# 📥 Installation

1. Download the latest **OOS15_Haptic_Fix_v1.5.zip**
2. Open **Magisk**, **KernelSU**, or **APatch**
3. Flash the module
4. Wait for installation to finish
5. Reboot the device

---

# ❓ FAQ

### Q: Why didn't standard haptics work?

The Nord 3 framework requests **RichTap / LMVibrator** effects that don't exist on MT6835 devices.

This module redirects those requests to the stock vibrator HAL instead.

---

### Q: Why didn't screen-off fingerprint work?

The port assumes an optical fingerprint sensor.

When the display turns off, Android disables the side-mounted fingerprint listener.

Setting:

```properties
persist.vendor.fingerprint.optical.support=0
```

forces Android to keep monitoring the side fingerprint sensor.

---

# 👑 Credits

| Role | Name |
|------|------|
| Developer | Ayan (@imnotaino) |
| Device Base | Realme  11 5G (chongqing) |
| Port Base | OnePlus Nord 3 (OxygenOS 15/16) |

---

# 📢 Telegram

### 👉 https://t.me/colorosmodules

---

<div align="center">

## ⚡ Restored Haptics. Fixed Fingerprint. Built for Port ROMs.

Made with ♥ by Ayan

</div>
