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
the Nix configuration and restart Rectangle. Build and flash the updated left
firmware to use the new keyboard bindings.
