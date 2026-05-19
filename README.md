# Ender 5 Plus — Klipper Stock Screen Compatibility
> **Status: Work In Progress**

This document tracks the current state of stock screen (DGUS/T5UID1) functionality running alongside Klipper on the Ender 5 Plus. Configuration changes and updates are versioned in this repository.

---

## ✅ Working Functions

### Temperature
- **Manual control** — Bed and Extruder temperatures can be set and adjusted manually via the screen

### Print
- **File Selection** — Browsing and selecting files for print functions correctly

### Settings

#### Move
- **Home** — Functions correctly
  > ⚠️ Requires a homing operation to be completed before movement controls become available

#### Other
- **Reset EEPROM** — Works as expected
- **Steppers** — Enable and Disable both function correctly

---

## ❌ Not Yet Working

### Temperature
- **Presets** — Does not apply temperatures
  > Requires macros to be defined in Fluidd configuration to handle preset targets

### Settings
- **Reset BLTouch** — Behaviour unknown / not yet investigated
- **Bed Leveling** — Button does nothing; likely requires a macro mapped to the screen command

---

## Notes

- Screen firmware: `dgus_reloaded` via `[t5uid1]` Klipper module
- Klipper config is maintained in this repository alongside this status document
- Investigations into non-working features are ongoing

### History
```
apt update && apt upgrade
apt -y install make cmake gcc git build-essential vim
reboot
git clone https://github.com/dw-0/kiauh.git
git clone https://github.com/doood81-arch/klipper-v0.13.0-t5uid1-E5P.git
cd kiauh ; ./kiauh.sh
reboot
ls -l /dev/serial/by-id/
rsync -avp --exclude=test/ ../dev/klipper-v0.13.0-t5uid1-E5P/klippy/extras/t5uid1 klippy/extras/
rsync -avp --exclude=test/ ../dev/klipper-v0.13.0-t5uid1-E5P/src/generic/t5uid1 src/generic/
rsync -avp ../../../dev/klipper-v0.13.0-t5uid1-E5P/src/avr/t5uid1 .
make menuconfig
make
sudo service klipper stop
make flash FLASH_DEVICE=/dev/serial/by-id/usb-1a86_USB2.0-Serial-if00-port0
sudo service klipper start
```

---

*Last updated: WIP*

---------------------

Welcome to the Klipper project!

[![Klipper](docs/img/klipper-logo-small.png)](https://www.klipper3d.org/)

https://www.klipper3d.org/

The Klipper firmware controls 3d-Printers. It combines the power of a
general purpose computer with one or more micro-controllers. See the
[features document](https://www.klipper3d.org/Features.html) for more
information on why you should use the Klipper software.

Start by [installing Klipper software](https://www.klipper3d.org/Installation.html).

Klipper software is Free Software. See the [license](COPYING) or read
the [documentation](https://www.klipper3d.org/Overview.html). We
depend on the generous support from our
[sponsors](https://www.klipper3d.org/Sponsors.html).
