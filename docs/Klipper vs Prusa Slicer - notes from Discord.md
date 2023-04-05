# Klipper vs. Prusa Slicer tips and info

```config
[printer]
kinematics: cartesian
max_velocity: 250
max_accel: 1800
max_accel_to_decel:1800
max_z_velocity: 25
max_z_accel: 100
square_corner_velocity: 5.0

[stepper_x]
full_steps_per_rotation: 200
homing_retract_dist: 0
homing_speed: 50
microsteps: 32
rotation_distance: 40
second_homing_speed: 3

[stepper_y]
full_steps_per_rotation: 200
homing_retract_dist: 0
homing_speed: 50
microsteps: 32
rotation_distance: 40
second_homing_speed: 3

[stepper_z]
full_steps_per_rotation: 200
homing_retract_dist: 5.0
homing_speed: 10
microsteps: 32

[extruder]
filament_diameter: 1.750
full_steps_per_rotation: 200
gear_ratio: 67:22
max_extrude_only_distance: 90
microsteps: 32
nozzle_diameter: 0.400
pressure_advance: 0.378
# Titan Extruder ->
rotation_distance:23.953
```

## Speed/acceleration tips

- You can print 60-70 at 5000 if you wanted. It is about acceleration, not so
  much speed

- You can check current Klipper acceleration with SET_VELOCITY_LIMIT command

- Speed is nothing,if you don't have the acceleration to get there at each move.
  And also check minimum layer time and use Prusa's speed view to see where you
  are slower

- "General" -> "How to apply limits" -  TIME ESTIMATE ONLY

- if you disable acceleration control in slicer, then klipper will use *its*
  defaults, set in `[printer]` {from config} this might be too high for normal
  printing

- For acceleration use the ones in `[print]` settings tab, not `[printer settings]`

- there is no jerk in klipper. klipper was written to take most standard gcode
  from a slicer

- "Maximum acceleration when extruding" applies to whole printer if told to;
  it's not "Extruder acceleration"

- Maximum volumetric speed (MVS) formula: Layer Height × Extrusion Width × Extruder Speed

- Settings which directly conflict with PA: seam gap, extra retract distance

- [Acceleration/speed calculator](https://blog.prusa3d.com/calculator_3416/#acceleration)

- [klipper_estimator](https://github.com/Annex-Engineering/klipper_estimator)

- Suggested speeds from TeachingTech's [Calibration Guide](https://teachingtechyt.github.io/calibration.html#retraction)
  - perimeters 60%
  - solid infill 80%
  - travel moves: 166%
  - first layer: 50%

## Invalid M204

> any ideas why i am getting spammed by Invalid M204 even though P is specified?
>
> `// Invalid M204 command "M204 P1000 ; adjust acceleration"`

because of the comments after it

## Slow speeds

- Check Prusa's "Maximum accelerations"
- check your minimum layer time {5 sec}, it might be limiting you, i use the
  speed feature screen in PS a lot, to adjust settings to get the right speeds
- otherwise you will be whatever max_accel you have set 100% of the time
- filament settings -> cooling -> cooling thresholds -> slow down if layer print
  time is below
- check if and what value is set there. sounds like your layer times are too
  short so that this setting takes effect

- Filament settings -> Cooling -> Cooling thresholds

  ```config
  Enable fan... 60
  Slow down... 5
  Min print speed 10
  ```

- if the speed that is using "min. print speed"{?}, then you have to lower the
  "slow down if layer print time is below:" which is above the min print speed

- Also check max volumetric flow under print settings and filament

## Example start print macro

```gcode
G90 ; use absolute coordinates
M82 ; use absolute distances for extrusion
G21 ; set units to millimeters
M220 S100 ; reset speed

M104 S170 ; set extruder no-ooze temp
M140 S85  ; set bed PINDA warmup temp

G28 ; Home
G0 X0 Y0 Z5 F4000; Raise nozzle to avoid denting bed while nozzle heats

M190 S85 ; wait for bed final temp
M109 S240 ; wait for extruder final temp
```

## Troubleshooting profiles

Just for comparison, use their default Prusa MK3S profile with their default
Prusament profile.  That's one way to rule out any weirdness with changes you
may have made to your specific profiles

## Bridges not detected

- "Quality (slower slicing)"
  - "Detect bridging perimeters" ON!!

## Moonraker/Octoprint compat

[octoprint_compat](https://moonraker.readthedocs.io/en/latest/configuration/#octoprint_compat)

## Infill contact with perimeters, Cura vs PS

"Horizontal skin expansion" = "Anchor solid infill by X mm"
