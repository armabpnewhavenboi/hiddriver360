# hiddriver360 prebuilt: wired + wireless XInput fixes (Vader 4 Pro)

**Download:** [hiddriver.xex](https://github.com/armabpnewhavenboi/hiddriver360/raw/builds/hiddriver.xex)

SHA-256: `27eac50d5df97e31e7899ef18ad208e3f3f2185127dde385cf43405c4c2b9573`

Built from commit `ab52bf9` on the [`fix-wired-xinput-pads`](https://github.com/armabpnewhavenboi/hiddriver360/tree/fix-wired-xinput-pads) branch.

Prebuilt `hiddriver.xex` from PR [EinTim23/hiddriver360#123](https://github.com/EinTim23/hiddriver360/pull/123). It lets wired and wireless third-party XInput controllers work on an RGH/JTAG Xbox 360 without an adapter. Tested with a Flydigi Vader 4 Pro, both on the cable and through its 2.4 GHz dongle.

### What's fixed
- **Wired XInput pads now receive input while hiddriver360 is loaded.** Previously only the Guide button worked. This affects genuine Microsoft wired controllers as well.
- **Pads that send input reports longer than 20 bytes now work.** The Vader 4 Pro sends 32 bytes (the standard 20 plus motion data), and the stock driver discarded them.
- **The Vader 4 Pro dongle no longer freezes the console.** It starts in a multi-interface HID mode before switching to XInput, and that start-up mode is now left alone.
- **HID controller setup is safer.** Only one interface is set up at a time, and only one per device. A crash on a bad report descriptor is also fixed.

### Requirements
- Dashboard **17559** on an RGH/JTAG console
- The **UsbdSec patch**, either selected in J-Runner when you build your NAND or loaded as the [UsbdSecPatch](https://github.com/InvoxiPlayGames/UsbdSecPatch) Dashlaunch plugin
- Controller set to **XInput / PC mode**

### Install
1. Copy `hiddriver.xex` to your console's HDD, for example `Hdd:\hiddriver.xex`.
2. In `launch.ini`, under `[Plugins]`, add a line pointing to it, for example `plugin1 = Hdd:\hiddriver.xex`. Remove any older hiddriver line.
3. Fully power off, then power on again.
4. Plug in the controller (wired), or plug in the dongle. **The dongle takes about 5 seconds to switch over before it responds.** This is normal.

This is an unofficial build until the PR is merged upstream.
