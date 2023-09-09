# Klipper on Tenlog TLD3 Pro
This is a work in progress to control the Tenlog TL-D3 Pro printer with Klipper.
AKA: HICTOP D3 Hero / Hellbot Hidra Plus

## Configuration
Make sure to modify the basic configuration to match your printer, and your Klipper installation.

| file | section |
| ------ | ------ |
| printer.cfg | mcu serial path |
|extruders.cfg| calibrate rotation_distance, (*)pressure_advance
|steppers.cfg|calibrate rotation_distance|
|positioning.cfg|if you don't have a probe, comment bltouch, bed_mesh and z_tilt sections|
> (*) Note: you must calibrate pressure advance on your own, and fill that value.

Then, calibrate the probe, and make sure to renew the bed mesh using the bedmesh_renew macro.
The current printer.cfg has my saved bed mesh for 50, 60 and 70 temperature settings. 

## Slicer Config
The Start and Stop gcodes are originally intender to use with SuperSlicer, but I've tested on Cura and works well too:
Start G-Code
```sh
prep_print EXTRUDER={first_layer_temperature[initial_extruder] + extruder_temperature_offset[initial_extruder]} BED={first_layer_bed_temperature} CHAMBER={chamber_temperature} FILAMENT={filament_type} COUNT={total_layer_count} TOOLS={total_toolchanges} NUM=1;Load print settings
```

End G-Code:
```sh
END_PRINT
```

## Notes
If you check the extruders.cfg config file, you will find that I'm using the 1.64 value for filament diameter. I measure the real diameter of the filament to make the test, this is a try to avoid any external factor to mess up my tests. But if you want to use the standard 1.75 value, is up to you, check the macro PREP_PRINT at the macros.cfg file too.

## Sources and References
This is a mix of existing configurations that I've found searching over all the Internet, but the primary sources are:
https://github.com/jonpackard/klipper_config_tld3pro/tree/master
https://github.com/matti125/klipper_config

And the Klipper documentation.
Also, my first try with this running on Klipper, was on the Creality Sonic Pad, so, I'd flashed the firmware through it.


