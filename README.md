# LedController V2 — PCB

Hardware design for the second revision of the LED controller: a mains-powered
ESP32-C6 board with an onboard AC-DC supply, USB-C, and header breakouts for the
LED outputs.

KiCad 9 project. Open `LedControllerPCB/LedControllerPCB.kicad_pro`.

---

## Status

**Schematic complete, PCB layout not started.** The `.kicad_pcb` file is an empty
board — treat this repo as the circuit design, not a manufacturable board yet.
Fabrication files, gerbers and 3D renders will land here when the layout is done.

## What's on the board

| Block | Part |
|---|---|
| MCU | ESP32-C6-WROOM-1 module (Wi-Fi 6 / BLE / 802.15.4) |
| Power | HLK-PM01 — isolated AC-DC module, mains in, 5 V out |
| Regulation | 3.3 V rail from the 5 V output |
| USB | USB-C receptacle, 16-pin, USB 2.0 only |
| ESD | USBLC6-2SC6 on the USB data lines |
| Timing | ABS25 32.768 kHz crystal for the RTC |
| I/O | 2×03 and 2×05 headers for the LED drive and expansion |
| Control | Reset and user push-buttons, 10 kΩ pull-ups |

**Mains safety:** the HLK-PM01 takes 230 V AC directly. Board clearances,
fusing and isolation on the mains side are the parts that matter most here — do
not build this without reviewing them.

## Relation to the firmware

This is the hardware half of the LED controller. The ESP32 firmware — ESP-IDF,
MQTT, Home Assistant discovery — lives in
[LedController](https://github.com/michaljj/LedController). Revision 1 was a
dev-board prototype; this board integrates the supply and the output stage.

---

## License

Licensed under the [PolyForm Noncommercial License 1.0.0](LICENSE.md). Free for
personal, academic and other noncommercial use. Commercial use requires a separate
license — get in touch.
