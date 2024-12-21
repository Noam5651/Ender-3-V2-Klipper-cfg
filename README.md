###fluidd set
[include gcode_macro.cfg]
[virtual_sdcard]
path: /usr/data/printer_data/gcodes

[display_status]

[pause_resume]

[stepper_x]
step_pin: PC2
dir_pin: PB9
enable_pin: !PC3
microsteps: 16
rotation_distance: 40
endstop_pin: ^PA5
position_endstop: 0
position_max: 235
homing_speed: 80

[stepper_y]
step_pin: PB8
dir_pin: PB7
enable_pin: !PC3
microsteps: 16
rotation_distance: 40
endstop_pin: ^PA6
position_endstop: 0
position_max: 235
homing_speed: 80

[stepper_z]
step_pin: PB6
dir_pin: !PB5
enable_pin: !PC3
microsteps: 16
rotation_distance: 8
endstop_pin: probe:z_virtual_endstop  #enable to use bltouch
# endstop_pin: ^PA7   #disable to use bltouch
# position_endstop: 0.0  #disable to use bltouch
position_max: 250
position_min: -10
homing_speed: 4
second_homing_speed: 1
homing_retract_dist: 2.0

[extruder]
max_extrude_only_distance: 1000.0
step_pin: PB4
dir_pin: PB3
enable_pin: !PC3
microsteps: 16
rotation_distance: 7.531
nozzle_diameter: 0.400
filament_diameter: 1.750
heater_pin: PA1
sensor_type: EPCOS 100K B57560G104F
sensor_pin: PC5
control: pid
 #tuned for stock hardware with 200 degree Celsius target
pid_Kp: 29.291
pid_Ki: 1.743
pid_Kd: 123.021
min_temp: 0
max_temp: 300
pressure_advance_smooth_time: 0.04
pressure_advance: 0.03

[heater_bed]
heater_pin: PA2
sensor_type: EPCOS 100K B57560G104F
sensor_pin: PC4
control: pid
# tuned for stock hardware with 50 degree Celsius target
pid_Kp: 67.104
pid_Ki: 0.544
pid_Kd: 2068.466
min_temp: 0
max_temp: 130

[filament_switch_sensor filament_sensor]
pause_on_runout: True
switch_pin: !PA4

[output_pin fan0]
pin: PA0
pwm: true
cycle_time: 0.0100
hardware_pwm: false
value: 0.00
scale: 255
shutdown_value: 0.0

[mcu]
serial: /dev/ttyS1
baud: 230400
restart_method: command

[printer]
kinematics: cartesian
max_velocity: 300
max_accel: 5000
max_z_velocity: 10
max_z_accel: 1000
square_corner_velocity: 5.0

[mcu rpi]
serial: /tmp/klipper_host_mcu

[bl24c16f]
i2c_mcu: rpi
i2c_bus: i2c.2
i2c_speed: 400000

[adxl345]
cs_pin: rpi:None
spi_speed: 2000000
spi_bus: spidev2.0

[resonance_tester]
accel_chip: adxl345
accel_per_hz: 70
probe_points:
    117.5,117.5,10

[input_shaper]
shaper_type_x = mzv
shaper_freq_x = 89.8
shaper_type_y = mzv
shaper_freq_y = 35.2

[bltouch]
sensor_pin: ^PB1
control_pin: PB0
x_offset: -31.8
y_offset: -49.5
#z_offset: 0
speed:35
samples:1
samples_result: median
samples_tolerance: 0.0075
samples_tolerance_retries: 10
probe_with_touch_mode: true
stow_on_each_sample: false
   
[safe_z_home]
home_xy_position: 145,160 # Change coordinates to the center of your print bed
speed: 150
z_hop: 10               # Move up 10mm
z_hop_speed: 10

[bed_mesh]
speed: 120
mesh_min: 30,30         #need to handle head distance with bl_touch
mesh_max: 180,180       #max probe range
probe_count: 5,5
fade_start: 1
fade_end: 10
fade_target: 0
algorithm: bicubic

[bed_screws]
screw1:30,25
screw1_name:1
screw2:200,25
screw2_name:2
screw3:200,195
screw3_name:3
screw4:30,195
screw4_name:4

[gcode_arcs]
#resolution: 1.0

#*# <---------------------- SAVE_CONFIG ---------------------->
#*# DO NOT EDIT THIS BLOCK OR BELOW. The contents are auto-generated.
#*#
#*# [bed_mesh default]
#*# version = 1
#*# points =
#*# 	-0.030000, -0.012500, -0.027500, -0.017500, -0.050000
#*# 	-0.022500, -0.020000, -0.020000, -0.012500, -0.045000
#*# 	0.012500, -0.000000, -0.015000, -0.002500, -0.035000
#*# 	-0.050000, -0.047500, -0.037500, -0.000000, -0.017500
#*# 	-0.052500, -0.065000, -0.057500, -0.027500, -0.047500
#*# x_count = 5
#*# y_count = 5
#*# mesh_x_pps = 2
#*# mesh_y_pps = 2
#*# algo = bicubic
#*# tension = 0.2
#*# min_x = 29.999999999999996
#*# max_x = 180.0
#*# min_y = 30.0
#*# max_y = 180.0
#*#
#*# [bltouch]
#*# z_offset = 3.370