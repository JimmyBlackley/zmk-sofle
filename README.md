# Sofle

## Update List

- 2024/12/21
  1. Added support for zmk-studio (just refresh the left hand to use).
- 2024/10/24
  1. Modified power supply mode to reduce power consumption.
  2. Fixed the automatic shut-off feature for RGB power supply.
- 2025/3/30
  1. Increased sleep entry time to 1 hour, added debounce time, optimized power consumption after sleep.
- 2025/8/22
  1. Updated soft off feature. Press and hold Q, S, and Z keys simultaneously for 2 seconds to enter deep sleep (cannot wake with key press, use reset switch to wake).
  2. Updated low-profile Sofle and Corne cases with thicker frame and bottom plate, adjusted reset switch opening.
  3. Removed GIF animation from right keyboard screen to significantly reduce power consumption.

> If your keyboard was updated before August 22, 2025, please update to the latest firmware.

---

# Contact Me

For 3D printed model files or any issues and malfunctions with the keyboard, please contact 380465425@qq.com

# Sofle Keymap

![Sofle键位图](keymap-drawer/eyelash_sofle.svg)

## Rectangle shortcuts

Hold **UPPER** and **left Ctrl** (the key beside Z), then press:

| Physical key | UPPER key | Rectangle action | Sent shortcut |
| --- | --- | --- | --- |
| I | Up | Top Half | Control + Option + Up |
| K | Down | Bottom Half | Control + Option + Down |
| J | Left | Left Half | Control + Option + Left |
| L | Right | Right Half | Control + Option + Right |
| , (below K) | Insert | Center Half | Control + Option + , |

UPPER and Ctrl can be held in either order. Without Ctrl, UPPER keeps its
normal arrows and Insert; the HOME comma is unchanged.

The four arrow shortcuts match `~/.config/nix/dotfiles/rectangle/RectangleConfig.json`.
Center Half uses `centerHalf` with key code `43` and modifier flags `786432`
(Control + Option). Import the updated JSON in Rectangle's settings, or apply
the Nix configuration and restart Rectangle. Flash the updated firmware to use
the new keyboard bindings.

## Firmware and Studio

This configuration merges upstream `cad1477` and targets the basic Sofle without
encoders, dials, or pointing devices. It uses the `nice_nano_v2` board with local
`eyelash_sofle_left` and `eyelash_sofle_right` shields. The right display keeps
the custom nice-view-dbz module. Firmware and module versions are pinned in
`config/west.yml`.

The left firmware supports ZMK Studio and DYA Studio over USB. DYA adds controls
for Bluetooth profiles and sleep/idle settings; settings changes also reach the
right half. Encoder remapping, pointing processors, and battery-history modules
are omitted for this hardware.

1. Build both halves using the **Build ZMK firmware** GitHub Actions workflow,
   or use the validated local UF2 files.
2. Double-tap each half's reset button to enter its UF2 bootloader. Copy
   `eyelash_sofle_studio_left.uf2` to the left half and
   `eyelash_sofle_right.uf2` to the right half.
3. Connect the left half by USB and open https://zmk.studio/ or
   https://studio.dya.cormoran.works/ in Chrome/Edge. Select the Sofle's USB
   serial port. Studio locking is disabled in this build.
4. If the keyboard output is set to Bluetooth, hold **LOWER + A** to select
   USB output before connecting Studio. USB Studio uses the active USB output.

Earlier firmware may expose two serial ports: the console port does not answer
Studio requests. During the local connection check, the installed firmware
answered Studio on `/dev/cu.usbmodem211304`, while `211301` was the other port.
This new build exposes only the Studio serial port.

If you previously saved a keymap using Studio, **Restore Stock Settings** loads
the compiled keymap after flashing and replaces those saved mappings. Ordinary
key assignments can then be edited and saved through Studio without flashing;
adding new behavior definitions still requires rebuilding firmware.
