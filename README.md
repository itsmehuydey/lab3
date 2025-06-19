# PROFILE INSTRUCTION

How to create and config viersc profile for specific motor  
All informations below are based on **rev0.2.3** branch

## Must have Predefines

Example for **XXX** motor

```
#ifndef HW_XXX_H_
#define HW_XXX_H_

#include "hw_build.h"
```


## DISABLE_HW_LIMITS

Unlock all locked features

## Define Motor Type

Define Motor Type:

- Hub Motor (Motor in Wheel)  
- Mid Motor (External Motor)

| DEFINE            | DESCRIPTION               | VALUE | DEFAULT / NOT DEFINE |
| ---------------- | ------------------------- | ----- | -------------------- |
| USE_HUB_MOTOR     | Enable to use hub motor    |       |                      |
| USE_ANANDA_MOTOR  | Enable to use ananda motor |       |                      |

Depends on motor type, define **USE_XXX_MOTOR**

## DEFINE MOTOR CONFIG and APP CONFIG

Defines can be found in **_conf_general.h_**

| DEFINE               | DESCRIPTION                    | VALUE | DEFAULT / NOT DEFINE |
| -------------------- | ------------------------------ | ----- | -------------------- |
| USE_350W_HUB_MOTOR   | Config for 350W hub motor       |       | Use config default from VESC default lib below:<br>```<br>#include "mcconf_default.h"<br>#include "appconf_default.h"<br>``` |
| USE_250W_HUB_MOTOR   | Config for 250W hub motor       |       |                      |
| USE_STELLA_250       | Config for Stella 250 motor     |       |                      |
| USE_STELLA_U_250     | Config for Stella U 250 motor   |       |                      |
| USE_U_LITE_XD48      | Config for U Lite - XD48 motor  |       |                      |
| USE_STELLA_U_LITE_XD | Config for Stella U Lite - XD   |       |                      |
| USE_U_LITE_NW        | Config for U Lite New motor     |       |                      |
| USE_STELLA_F250      | Config for Stella U F250 motor  |       |                      |
| USE_XOFO_R_250       | Config for Xofo R 250 motor     |       |                      |
| USE_XOFO_R_350       | Config for Xofo R 350 motor     |       |                      |
| USE_600W_MID_MOTOR   | Config for 600W Mid motor       |       |                      |
| USE_AIOT_T1_MOTOR    | Config for AIOT T1 motor        |       |                      |
| USE_EAGLE_T7         | Config for Eagle T7 motor       |       |                      |
| USE_ANANDA_MOTOR     | Config for mid/ananda motor     |       |                      |
| USE_LFASTER_350      | Config for LFaster 350 motor    |       |                      |
| USE_AKM_250          | Config for AKM 250 motor        |       |                      |
| USE_FALCON_MOTOR     | Config for Falcon motor         |       |                      |

## DEFAULT_WHEEL_DIAMETER

Wheel Size Diameter  
Define can be found in **app_adc_pas.c**

Use wheel size diameter to change duty cycle for the motor follow the calculation below

Duty cycle = 0.2 * 0495f / DEFAULT_WHEEL_DIAMETER

| DEFINE                 | DESCRIPTION           | VALUE                  | DEFAULT / NOT DEFINE                        |
| ----------------------| --------------------- | ---------------------- | ------------------------------------------ |
| DEFAULT_WHEEL_DIAMETER| Wheel size diameter   | From 0.390f to 0.760f  | If it’s not define, the motor will use 20% duty cycle |

## HW_USE_WHEEL_SPEED_SENSOR

Define MC state that has speed sensor or not
Ensure the motor operations are true when it doesn't have the speed sensor

## HW_USE_WHEEL_SPEED_SENSOR x
With x value is 1 for have and 0 for doesn’t have

## ENABLE_LIMIT_SPEED
Enable the speed limit with an available threshold (this threshold often is 25KPH and depends on PAS levels)  
Specific detail in `app_adc_pas.c`

#define ENABLE_LIMIT_SPEED x

With x value is `1 for enable` and `0 for disable`

## USE_UNLIMIT_SPEED
Set speed threshold = **99 KPH**

## USE_LIMIT_SPEED_25KPH

Set speed threshold = **25 KPH**

## RPM_2_ERPM
Define in `hw_viersc_core30.c`  
This is an ERPM ratio to calculate RPM

#define RPM_2_ERPM x

With x is a value in range from 60 to 99

## USE_APP_DISPLAY

Define to enable app display for screen

| DEFINE           | DESCRIPTION        | VALUE                                | DEFAULT / NOT DEFINE              |
| ---------------- | ------------------ | ------------------------------------ | --------------------------------- |
| USE_APP_DISPLAY  | Enable app display | If it's defined, use app with display | If isn’t defined, use app without display |

## Cadence definitions

Define cadence config  
Refer to definitions in `app.h`

| DEFINE                    | DESCRIPTION              | VALUE                                                | DEFAULT / NOT DEFINE |
| -------------------------| ------------------------ | ---------------------------------------------------- | -------------------- |
| ENABLE_CADENCE           | Enable cadence           | If it's defined, app init with cadence               | If isn’t defined, app init without cadence |
| CADENCE_TYPE_DEFAULT     | Define cadence type      | CAD_1WIRES<br>CAD_2WIRES                             | CAD_2WIRES           |
| CADENCE_PULSES_DEFAULT   | Define cadence pulse     | NO_CADENCE<br>CAD_8_PULSES<br>CAD_12_PULSES<br>CAD_16_PULSES<br>CAD_18_PULSES<br>CAD_24_PULSES<br>CAD_28_PULSES<br>CAD_32_PULSES<br>CAD_36_PULSES | CAD_18_PULSES        |
| CADENCE_DIRECTION_DEFAULT| Define cadence direction | CAD_DIR_FW<br>CAD_DIR_RW                             |                      |

## Ramp up ERPM

| DEFINE                | DESCRIPTION                | VALUE              | DEFAULT / NOT DEFINE |
| ---------------------| -------------------------- | ------------------ | -------------------- |
| USE_RAMP_UP_ERPM     | Enable ramp up ERPM for motor | True (Enable ramp up) | Disable ramp up      |
| MAX_ERPM_SET         | Set high limit for ERPM     | About 100000        |                      |
| MIN_ERPM_SET         | Set low limit for ERPM      | About 10000         |                      |
| USE_RAMP_UP_ERPM_TIME| Set time to execute ramp up | About 2.0 (second)  |                      |



