<a href='https://postimg.cc/GHqW5Jnj' target='_blank'><img src='https://i.postimg.cc/GHqW5Jnj/Screenshot-2026-02-16-9-50-46-PM-removebg-preview.png' border='0' alt='Screenshot-2026-02-16-9-50-46-PM-removebg-preview'></a>
<!-- ok what is happening -->
**Z0DIAC** is a work-in-progress experimental bootloader environment for ChromeOS RMA/recovery media that allows booting multiple Linux root filesystems from a single recovery USB.

---

## What Z0DIAC Is

* A research project exploring ChromeOS RMA shim boot behavior
* A multi-distro Linux launcher using a ChromeOS-compatible kernel
* A recovery-USB-based environment (no firmware flashing required)
* A pivot_root-based boot transition system
* Designed to experiment with:

  * Debian
  * Ubuntu
  * Arch Linux
  * Alpine
  * Other compatible rootfs builds
  * Optionally returning to ChromeOS when supported

---

## What Z0DIAC Is Not

* Not an unenrollment tool
* Not a bypass for enterprise management
* Not malware
* Not a firmware exploit toolkit
* Not a universal Linux installer for locked devices
* Not intended to circumvent ownership controls

Z0DIAC does **not** modify device firmware and does **not** remove device management.

---

## Project Overview

Z0DIAC is built around this concept:

```
ChromeOS-compatible kernel
        │
        ▼
Minimal initramfs
        │
        ▼
Boot menu (select distro)
        │
        ▼
Mount selected rootfs
        │
        ▼
pivot_root → start init system
```

The system:

1. Boots using a ChromeOS-compatible recovery/RMA kernel.
2. Loads a lightweight custom initramfs.
3. Presents a boot menu for distro selection.
4. Mounts the selected Linux root filesystem.
5. Switches into that system using `pivot_root`.
6. Launches the distro’s init system (systemd, OpenRC, etc.).

All of this runs entirely from external media.

---

Root filesystems may be:

* Separate partitions
* Loop-mounted disk images
* SquashFS compressed images
* Encrypted volumes (planned)

---

## Planned Distro Support

Z0DIAC aims to support:

* Debian (stable/testing/unstable)
* Ubuntu
* Arch Linux
* Alpine Linux
* Custom rootfs builds

Support depends on compatibility with:

* ChromeOS kernel configuration
* Available firmware blobs
* Device-specific drivers

---

## Known Limitations

Because Z0DIAC relies on a ChromeOS-compatible kernel:

* Suspend may not work
* Swap may be disabled
* Audio may require manual firmware configuration
* Some GPUs may require legacy Mesa drivers
* Certain devices may block external recovery boot

Hardware compatibility varies by Chromebook board.

---

## Security and Ethics

Z0DIAC is designed for:

* Research
* Educational purposes
* for developers and for curious people!

Z0DIAC **ISN'T:** 

* Circumventing enterprise controls
* Removing enrollment
* Modifying device ownership status

Users are responsible for complying with all local laws and device ownership policies.

---

## Credits

What inspired me to do this was Shimboot, basically the same thing as this, but with less versions and stuff. 

https://shimboot.ading.dev
https://github.com/ading2210/shimboot

Although this project is completely seperate from Shimboot, it might look a bit similar. Dont worry! I won't, don't, and ever will take their code without permission, and I probably won't ask for permission anyway ^-^

---

## License

this project uses the GNU General Public License, and it states that, in simpler terms, no one is allowed to take this and call it theirs.
just use it i dont fucking care just dont call it yours or go fuck yourself
