# FlashGuard_SFG-Prototype

🏷️ **BRANDING & ABOUT (SFE LLC)**

* **Product:** FlashGuard-v1_SFG-Prototype
* **Version:** v.01.1
* **Status:** SFG-Prototype
* **Created by:** [Jon Merriman / Juggalospsyco420 / GhostDragon420](https://github.com/GhostDragon420)

> This file is made by Sync-First Essentials LLC, where the Sync-First Idea Becomes Real!

---

## 🧠 Description

This is an early prototype of Sync-First Gate (SFG) as a Read-Only BIOS/Firmware data tool.
It does NOT flash or change anything on your PC — it only reads and logs data.

---

## 🎯 Goals

To make the chore of BIOS/ME flashing safer, faster, and more predictable.
Eventually with a single click, it will be able to take a snapshot of your
current firmware/hardware state, validate payloads/flashes, and most
importantly and safely restore your settings immediately after a successful reboot.

---

## ⚠️ ATTENTION

**This is a PRERELEASE PROTOTYPE ONLY.** It does NOT flash anything yet.
But it does create a "snapshot" in the format of a JSON file, can validate
a pretend payload/flash, and will show you where ME/EFI hooks should go.
**AGAIN — this is a PRERELEASE PROTOTYPE ONLY!**

---

## 🧠 What It Does

* Collects a hardware + BIOS snapshot (safe read-only)
* Checks a sample firmware file for compatibility
* Generates a post-flash "restore plan" (no flashing)

---

## 🔧 What It Will Do Today

* Collects a hardware/firmware snapshot using harmless commands such as WMI and PowerShell.
* Saves its results to `./state/snapshots/<hostname>-<timestamp>.json`
* Validates a mock firmware payload file (metadata file to look like a BIOS/Firmware Update)
* Prepares a "post-flash plan" with a boot order, a memory profile, and fan curve hints.

---

## 🗺️ Projected Roadmap (2025-2026)

**MEI / FW Tooling:**

* Detect Intel MEI driver + version (WMI device query).
* Add wrappers for FWUpdLcl64.exe (Intel ME firmware) and OEM BIOS CLI tools.

**EFI Variable I/O:**

* Read and copy settings like NVRAM: boot order, SecureBoot mode, Re-BAR, XMP status (vendor-specific) so as not to lose anything in case of a rollback.

**Policy Engine:**

* Compares pre-flash snapshot with the post-flash platform map so that it will reapply only safe params.

**Rollback:**

* Keeps the last known-good BIOS config + ME region checksum and will auto-rollback in case of failure.

---

## 💻 System Requirements

* Windows 10 or 11 (32-bit or 64-bit)
* Python 3.10 or newer installed

✅ Works on both x64 and x86 Windows systems.
Just make sure your Python version matches your Windows type:

* 64-bit Windows → 64-bit Python
* 32-bit Windows → 32-bit Python

Windows-only for now (PowerShell calls). Linux/Mac support planned.

---

## ⚙️ How to Use

1. Unzip the downloaded file anywhere.
2. Open the folder in File Explorer.
3. Right-click inside the folder → "Open in Terminal" or "Open PowerShell window here".
4. Run one of the following commands:

* **Create a system snapshot:**

```py
python flashguard-launcher.py snapshot
```

* **Validate a firmware payload (demo only):**

```py
python flashguard-launcher.py validate --payload samples/mock_firmware_payload.json
```

* **Create a restore plan:**

```py
python flashguard-launcher.py plan --xmp 3200 --boot YourDriveNameHere --rebar on
```

---

> 💡 In this prototype, the `--boot` value is only stored as text in the output plan.
> It does not change, write to, or interact with any drives.
> This is included only as a proof of concept showing how FlashGuard could
> remember your chosen boot device in a real version later.

---

## 🧱 Notes

* You can view results inside the "state" folder that appears after running it.
* The snapshot and plan files are saved in readable JSON format.
* This is read-only and safe. It does not write to any file other than the one you tell it to.
* All results will go to `./state/`
* This build is for demonstration and learning only.
* A standalone .EXE version will be added in a future update.

---

## 🛡️ Legal

* © 2025-2026 Jon Merriman / Sync-First Essentials LLC — All Rights Reserved
* This product is part of **Sync-First Essentials LLC**, built on the **Sync-First** idea made real.
* **Website:** [www.syncfirstessentials.com](https://www.syncfirstessentials.com)
* **Support:** [jon@syncfirstessentials.com](mailto:jon@syncfirstessentials.com)
