# AWD Mod 6mm for Mercury1.1 with [Metal Gantry mod](https://github.com/TurtleCrawler/Mercury-One.1---Full-Metal-Gantry/tree/main)

<img src="IMAGES/AWD_Assembly_Front.png">

# The mods are in testing, the parts may or may not fit right. I am not responsible for any damage this may cause.

# BOM:
| Type | Quantity | Link |
| --- | --- | --- |
| D5x M3 Length 10mm | 14 | [Aliexpress](https://www.aliexpress.us/item/1005005962614409.html) |
| D8x M5 Length 10mm | 2 | [Aliexpress](https://www.aliexpress.us/item/1005005962614409.html) |
| D5x M3 Length 20mm | 8 | [Aliexpress](https://www.aliexpress.us/item/1005005962614409.html) |
| M3 20mm | 6 | [Aliexpress](https://www.aliexpress.us/item/4000152799825.html) |
| F695-2RS bearings | 12 | [Fushi](https://www.aliexpress.com/item/32850989216.html) |
| 695-2RS bearings | 2 | [Fushi](https://vi.aliexpress.com/item/1005003141257945.html) |
| M3x 40 screws | 8 | [Nindejin](https://www.aliexpress.us/item/2255800006841202.html) |
| M3x 20 screws | 6 | [Nindejin](https://www.aliexpress.us/item/2255800006841202.html) |
| M3x 10 screws | 6 | [Nindejin](https://www.aliexpress.us/item/2255800006841202.html) |
| M5x 25 screws | 2 | [Nindejin](https://vi.aliexpress.com/item/4000142028043.html) |
| M5 T-nut | 2 | [Aliexpress](https://vi.aliexpress.com/item/32706208829.html) |
| M3 Heatset insert M3 X D5.0 X L4.0 | 2 | [Aliexpress](https://www.aliexpress.us/item/2255800046543591.html)  |
| 9mm tall gt2 20 tooth pulley | 2 | [Mellow](https://www.aliexpress.us/item/2251832836818881.html) |
| gt2 6mm belts | 6 Meters | [TriangleLab](https://www.aliexpress.com/item/1005006507781085.html) |
| GT2 20 tooth motor pulley for 6mm belt | 4 | [Mellow](https://vi.aliexpress.com/item/33023279793.html) |
| Motors with minimum 35mm shaft | 4 | [RatRig](https://ratrig.com/electronics/motors/nema-17-stepper-motor-ht-48mm-1-8-76oz-in-35mm-shaft.html) |
| stepper drivers available to drive the extra motors | 2 |  |

# Belt paths
**:warning:! You must flip the X-joints bearing stacks and pulleys upside down !:warning:**

## Bottom belt path

<img src="IMAGES/BottomBeltPath.png">

## Top belt path

<img src="IMAGES/TopBeltPath.png">

# How to sync motors

[VZbot Motor sync](https://www.youtube.com/watch?v=so9oqJyirKY)

# Printer config

-The X and Y motors are now swithed and rotating backwards because of the new belt path so the pins must be swithed 

-The front motors will be defined as stepper_x1 and stepper_y1 the step and dir pins will need to have the same sign in front ( both x and x1 sould have DIR and STEP pin with ! or without, same for y and y1)

-Lower the homing speed to 10 and the motor amps to 0.4 or as low as you cand get them to move so that you have time to stop the printer if it goes the wrong direction and minimize the damage if the endstop pins are wrong.

My config as an example:
```
[stepper_x]
step_pin: PC14
dir_pin: !PC13
enable_pin: !PE6
microsteps: 16
rotation_distance: 40
endstop_pin: ^EBBCan:PB6
position_endstop: 386
position_max: 386
homing_speed: 150

[tmc5160 stepper_x]
cs_pin: PD6
spi_software_sclk_pin: PC6
spi_software_mosi_pin: PC8
spi_software_miso_pin: PC7
#diag1_pin: PC15
run_current: 1.400
sense_resistor: 0.022
#stealthchop_threshold: 999999



[stepper_x1]
step_pin: PE2
dir_pin: !PE1
enable_pin: !PE0
microsteps: 16
rotation_distance: 40

[tmc5160 stepper_x1] 
cs_pin: PD4
spi_software_sclk_pin: PC6
spi_software_mosi_pin: PC8
spi_software_miso_pin: PC7
#diag1_pin: PF1
run_current: 1.400
sense_resistor: 0.022
#stealthchop_threshold: 999999


[stepper_y]
step_pin: PE5
dir_pin: !PE4
enable_pin: !PE3
microsteps: 16
rotation_distance: 40
endstop_pin: PC0
position_endstop: 370
position_max: 370
position_min: 0
homing_speed: 150

[tmc5160 stepper_y]
cs_pin: PD5
spi_software_sclk_pin: PC6
spi_software_mosi_pin: PC8
spi_software_miso_pin: PC7
#diag1_pin: PF0
run_current: 1.400
sense_resistor: 0.022
#stealthchop_threshold: 999999


[stepper_y1]
step_pin: PB9
dir_pin: !PB8
enable_pin: !PB7
microsteps: 16
rotation_distance: 40

[tmc5160 stepper_y1] 
cs_pin: PD3
spi_software_sclk_pin: PC6
spi_software_mosi_pin: PC8
spi_software_miso_pin: PC7
#diag1_pin: PF2
run_current: 1.400
sense_resistor: 0.022
#stealthchop_threshold: 999999
```
