FlashGuard-v1_SFG-Prototype README
This is an early prototype of Sync-First Gate(SFG) as a Read-Only BIOS/Firmware data tool. It does NOT flash or change anything on your PC — it only reads and logs data.

My Goals:
To make the chore of BIOS/ME flashing safer, faster, more predictable. And eventually with a single click, it will be able to take a snapshot of your current firmware/hardware state, and validate payloads/flashes. And most importantly and safely restore your settings immediately after sucessful reboot.

ATTENTION!!!!
This is a prerelease prototype only. It doesn’t flash anything yet. But it does create a “snapshot” in format of a JSON file, as ot va;odate a pretend payload/flashing and iwll show you were ME/EFI hooks should go. But AGAIN it is a PRERELEASE PROTOTYPE ONLY!!!!

What it will do today
It will collects a hardware/firmware snapshot using harmless commands such as WMI and PowerShell.
It will save its results here = ./state/snapshots/<hostname>-<timestamp>.json.
It will validat a mock firmware payload file which is metadata file to look like a BIOS/Firmware Update)
It will prepare a “post-flash plan” with a boot order, a memory profile, and fan curve hints.
Projected Roadmap (2025-2026)
MEI / FW Tooling
Detect Intel MEI driver + version (WMI device query).
Add wrappers for FWUpdLcl64.exe (Intel ME firmware) and OEM BIOS CLI tools.
EFI variable I/O
It will be able to Read and Copy setting lik NVRAM: boot order, SecureBoot mode, Re‑BAR, XMP status (vendor-specific) so as not to lose anything incase of a Rollback.
Policy Engine
Compares pre‑flash snapshot with the post‑flash platform map so that it will reapply only safe params.
Rollback
Keeps the last known-good BIOS config + ME region checksum and will auto-rollback incase of failure.
Usage & Notes
There is a detailed FlashGuard-v1_SFG-Prototype_Readme.md document in v.1_SFG-Protoyte that has a python launcher.
Windows-only for now (PowerShell calls). Linux/Mac support planned.
This is read-only and safe. It does not write to any file other than the one you tell it to and also,
All results will go to ./state/.
