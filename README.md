Here is a fully customized, professional **README.md** tailored specifically for the **OOS15 Haptic & Fingerprint Fix** (v1.5) release page:

```markdown
<div align="center">

# 📳 OOS15 Haptic & Fingerprint Fix

### Restore UI Touch Haptics, Gboard Vibration, and Screen-Off Fingerprint Unlock on Nord 3 Port ROMs
<img width="1774" height="887" alt="Haptic and Fingerprint Fix Cover" src="https://github.com/user-attachments/assets/65b2ff9e-221a-48e2-8c49-c0bb17c7e72e" />

<a href="https://github.com/Sairb1/MT6835_Optimizer/releases">
  <img src="https://img.shields.io/badge/Port%20Device-Realme%2011x%205G%20%7C%2011%205G-brightgreen?style=for-the-badge"/>
</a>

<a href="https://github.com/Sairb1/MT6835_Optimizer/releases">
  <img src="https://img.shields.io/badge/ROM-Nord%203%20Port%20(OOS15%2F16)-blue?style=for-the-badge"/>
</a>

<a href="https://github.com/Sairb1/MT6835_Optimizer/releases">
  <img src="https://img.shields.io/badge/Root-Magisk%20%7C%20KernelSU%20%7C%20APatch-orange?style=for-the-badge"/>
</a>

<a href="https://github.com/Sairb1/MT6835_Optimizer/releases">
  <img src="https://img.shields.io/badge/Android-15%2B-red?style=for-the-badge"/>
</a>

<a href="https://t.me/colorosmodules">
  <img src="https://img.shields.io/badge/Telegram-colorosmodules-229ED9?style=for-the-badge&logo=telegram"/>
</a>
<br/>

### Premium haptic restoration & side-fingerprint fixer for ported OxygenOS 15/16 ROMs

Made with ♥ by **[Ayan (@imnotaino)](https://t.me/imnotaino)**  
Updates & Support → **[t.me/colorosmodules](https://t.me/colorosmodules)**

</div>

---

# 📖 What is this?

**OOS15 Haptic & Fingerprint Fix** is a specialized Magisk/APatch/KernelSU module engineered specifically for MT6835 devices (like the **Realme 11x 5G / Realme 11 5G**) running ported **OxygenOS 15/16 (Nord 3 base) ROMs**.

When porting a ROM from a high-end device like the **OnePlus Nord 3** to budget-tier hardware, severe hardware-level mismatches occur:

### The Mismatch
| Feature | Nord 3 (Port Base) | Realme 11x / 11 (Your Device) | Mismatch Result |
|---|---|---|---|
| **Vibrator** | Premium Linear Motor HAL (`LMVibrator` / `RichTap`) | Standard Z-Axis/X-Axis Driver (`regulator_vibrator`) | **NO UI/Gboard Vibration** (Framework drops haptics searching for missing HAL) |
| **Fingerprint** | Under-Display Optical Sensor | Side-Mounted Capacitive Sensor | **NO Screen-Off Unlock** (System expects screen touch, ignores side sensor) |
| **Display** | AMOLED (with native AOD) | LCD Display (No AOD) | **Screen-off lag / battery drain** |

This module resolves these mismatches system-lessly by overriding the framework feature flags and calibration tables.

---

# ✨ Features

## 📳 UI & Gboard Haptic Restore
Bypasses the missing LMVibrator HAL and redirects haptic feedback back to the device's standard AIDL vibrator service:
- **Disables LMVibrator / RichTap / HapticV1** flags inside OPlus feature configurations.
- **Restores stock 75KB touch haptic waveforms** (`effect_waveform.xml`) instead of the truncated port version.
- **Injects the Gboard duration map** (`inputmethod_duration_map.xml`) to restore keyboard haptics.
- Resets the OPlus touch intensity property (`touch_stepless_vibration_intensity`) from the invalid `2400` value to a standard value of `2`.

## 🔑 Screen-Off Side Fingerprint Unlock
Forces the system keyguard to recognize and listen to the side capacitive fingerprint sensor when the screen is black:
- Overrides `persist.vendor.fingerprint.optical.support` to `0` at boot via `resetprop`.
- Comments out `oplus.software.fingeprint_optical_enabled` inside display and multimedia configurations.
- Restores quick, non-wake touch-to-unlock behavior from screen-off state.

## ⚡ Early Post-Mount Execution
Uses Magisk/APatch's early `post-mount.sh` boot phase to bind-mount the modified XML configs **before the Android `system_server` starts up**, ensuring the corrected feature flags are read and loaded into memory properly.

---

# ⚡ Premium Flashing Experience

Includes a fully customized flashing terminal UI featuring:
- Animated progress output
- Live device information parsing
- Android version detection
- Kernel version retrieval
- Battery percentage status
- Automatic Telegram channel launcher upon installation

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
          ★  Device  Info  ★
──────────────────────────────────────
  Device  : realme Narzo 60x 5G
  Codename: ossi
  Android : 15  (SDK 35)
  Build   : CPH2491_15.0.0.xxx
  Kernel  : 5.15.x
  Battery : 82%
──────────────────────────────────────

  ► Initializing fix engine...
  ► Disabling LMVibrator & RichTap HAL features...
  ► Restoring stock 75KB touch haptic waveforms...
  ► Commenting out optical fingerprint configurations...
  ► Injecting side capacitive fingerprint properties...
  ► Finalizing runtime configuration...

══════════════════════════════════════
      ✓ OOS15 Haptic & FP Fix Ready!
══════════════════════════════════════

  ➤  t.me/colorosmodules

  Made with ♥ by Ayan (@imnotaino)
```

---

# 📦 What the module modifies

The module dynamically overlays/mounts:
- `/my_product/etc/permissions/oplus.feature.android.xml`
- `/my_product/etc/permissions/oplus.product.feature_multimedia_unique.xml`
- `/my_product/etc/permissions/oplus.product.display_features.xml`
- `/my_product/etc/extension/com.oplus.oplus-feature.xml`
- `/my_product/etc/vibrator/effect_waveform.xml`
- `/my_product/etc/vibrator/effect2waveform.xml`
- `/my_product/etc/vibrator_service_config/inputmethod_duration_map.xml`

And overrides properties at boot:
- `persist.vendor.fingerprint.optical.support` → `0`
- `persist.sys.linearmotor.enable` → `0`
- `ro.oplus.vibrator.lmvibrator` → `false`
- `ro.vendor.vibrator.hal.lm` → `0`

---

# 📥 Installation

1. Download the latest `oos15_haptic_fix.zip` (v1.5) module.
2. Open **Magisk**, **KernelSU**, or **APatch**.
3. Flash the module zip.
4. Let the flash complete (it will auto-open the Telegram channel for support).
5. Reboot your device.

---

# ❓ FAQ

## Q: Why did standard haptics fail without this?
The ported ROM's apps (SystemUI, Launcher) request OPlus-specific RichTouch vibration IDs. The framework tried to play these through a native LMVibrator service which does not exist on your device. The module forces the framework to redirect these haptic requests to the standard vibrator HAL instead.

## Q: Why did side fingerprint fail when screen was black?
The Nord 3 ROM assumed the device had an under-display optical sensor. When the screen went off, it disabled the side capacitive touch listener. Setting `optical.support=0` forces the system to keep the side capacitive sensor active.

---

# 👑 Credits

| Role | Name |
|---|---|
| Developer | Ayan (@imnotaino) |
| Device Base | Realme 11x 5G / 11 5G (ossi) |
| Port Base | OnePlus Nord 3 OOS 15/16 |

---

# 📢 Telegram Channel

### 👉 https://t.me/colorosmodules

---

<div align="center">

## ⚡ Restored Haptics. Fixed Fingerprint. Built for Port ROMs.

Made with ♥ by Ayan

</div>
```
