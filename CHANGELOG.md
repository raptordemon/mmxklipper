# Changes by file

## macros.cfg
- revamped START_PRINT and END_PRINT to use Klipper commands for heating up. This will succeed much faster, as Klipper doesn't wait for the build plate to cool down from 56,1° to 55° when overshooting just a little bit. The cust
om GCode for starting prints in PrusaSlicer is

```START_PRINT T_TOOL={first_layer_temperature[0]} T_BED={first_layer_bed_temperature[0]}```

For Cura, sth similar exists, but i just don't use it anymore. :) 
I did not include any default values on purpose, so that the print just doesn't start when no Temp is set via Slicer.
- also removed SET_GCODE_OFFSET from start code as it interferes with any manual adjustment being done in mainsail
- removed LED commands as the Mingda doesn't have any from scratch. But feel free to re-add if it's actually used somehow
- added GCode to shut down heaters after bed leveling
- modified M600 to not use Filament Runout macros, but just pause
- changed bed mesh points to 3x3 as i find this absolutely sufficent for the bed size and spares a lot of time
- changed Temp for Bed Mesh leveling to 150° Nozzle and 50 bed. Above 150° the Filament starts drooling out of the nozzle, leaving ugly marks on the bed. With 150, it still is squishy enough to not interfere with the probing, but hard enough to not drool out.
- bed mesh p1 is loaded at print start, not leveling the bed every time. As the printer does not have adjustable wheels for the bed, measuring it once every now and then manually should be enough.


## printer.cfg
- removed comments and disabled options
- upped retry_tolerance to 0.05 to avoid too many z_tilt retries. Everything beyong 0.05 difference will be evened out with the bed mesh anyways
- set max temp to 110° as this is the max value told by Mingda
- removed Raspberry Pi-centric commands. If Klipper is running on sth else than a Pi (as in my case, using a small server), it will fail with those in place.
