# Beaglebone Black Adapter for mortr.io

## Reading gpios using `sysfs` files

GPIOs show up in `/sys/class/gpio/gpio*`. Each GPIO gets it's own directory. Description of files in directory:

- `active_low`: `1` for pulled low & `0` for not.
- `device/`: directory ???
- `direction`: `in` (input mode) or `out` (output mode)
- `edge`: Trigger on rising or falling edge (actual parameters ???)
- `power/`: directory ???
- `subsystem`: directory ???
- `uevent`: Empty ???
- `value`: State of the pin. Read or write `0` for LOW and `1` for HIGH (based on the programmed direction)

## Show ADC pins in `sysfs` on 4.0+ kernel

1. Install dtc (device tree compiler) on BBB: `apt-get install dtc`
2. Clone and install beaglebone overlays repo on BBB

	```
	git clone https://github.com/beagleboard/bb.org-overlays
	cd ./bb.org-overlays
	./dtc-overlay.sh
	./install.sh
	```
3. Load ADC DT-modules with: `echo 'BB-ADC' > /sys/devices/platform/bone_capemgr/slots`

Raw ADC values can be read from `/sys/bus/iio/devices/iio\:device0/in_voltageN_raw`.
