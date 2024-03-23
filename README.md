# dr2ds
Adaptive triggers, meet Dirt Rally 2. Dirt Rally 2, meet adaptive triggers.

![dr2ds screenshot](https://github.com/firelight322/dr2ds/blob/main/dr2ds-screenshot.jpg)
<!-- <img src="https://github.com/firelight322/dr2ds/blob/main/dr2ds-demo.gif" width="900" height="506"> -->

`dr2ds` is a simple tool to enable dual sense features when playing Dirt Rally 2. It has a few curves for the triggers and supports reading DR2 telemetry to add immersive effects.

[download latest](https://github.com/firelight322/dr2ds/releases/latest)



## Features
- Selection of curves for brakes and throttle.
	- Constant : Fixed force. Useful for throttle.
  	- Conventional Brakes : A formula I picked up from some white paper. Basically 2 stages.
	- Three Stage : Ramps up from soft to medium to hard strength.
	- Curve : Log, linear or exponential curve. Controllable through settings.
- Suspension effect.
	- Pushes back on the adaptive trigger when suspension compresses. Purely for immersion.
- Speed effect.
	- Adds more force the faster you go. Very nice on brakes.

## Installing
- Download the latest version from the release page.
- Double click the application to launch.
  - The first time `dr2ds` runs, it will create a default `dr2ds.ini` settings file.
  - You can open up the file and edit it while the app is running, it will update its settings.
  - Yes it is a terminal application, but you shouldn't need to know anything about command prompts to use it.
- The app should detect you controller and you should feel forces immediately.
- Enjoy!

## Telemetry Setup
To get telemetry feedback, you'll need to enable Dirt Rally UDP packets. But if you have problems with telemetry, you can still use the force feedback presets without it.

1. Navigate to your game folder, usually in `%userprofile%\Documents\My Games\DiRT Rally 2.0\hardwaresettings`
2. Open `hardware_settings_config.xml` in a text editor like notepad.
3. Look for a line starting with `<udp`.
4. Change it to this : `<udp enabled="true" extradata="3" ip="127.0.0.1" port="20777" delay="1" />`
  - Note, if you didn't find that line, add it to the `<motion_platform>` section.
5. If all goes well, it should detect both your controller and the game.

## dr2ds.ini
You can customize the behavior through the `dr2ds.ini` file. Most gamers have played around with ini files in the past, but if you haven't, there are comments explaining everything.
```ini

[Global Settings]

  ; The ini file version. Do not modify this.
version = 0

  ; When set to true, the brake settings are mapped to the right trigger and accel settings are mapped to the left trigger.
  ; Possible values : true or false.
flip_triggers = false

  ; Enables quitting application by pressing L1 + R1 at the same time.
  ; Possible values : true or false.
l1r1_exit = false

  ; This settings is used by the suspension push back effect.
  ; It is the ratio between the front and back suspensions.
  ; Possible values : 0.0 to 1.0 (percentage).
  ;   1.0 = front suspension only
  ;   0.0 = back suspension only.
suspension_effect_front_bias = 0.5

[Brake Settings]

  ; The simulation preset to use for this trigger.
  ; Possible values :
  ;   "constant"
  ;   "conventional_brakes"
  ;   "three_stage"
  ;   "curve"
preset = "conventional_brakes"

  ; The overall average force applied to the trigger.
  ; The simulation will try to cap the force to this value,
  ; but environment effects may push it over.
  ; When in 'constant' preset mode, this is the constant force value.
  ; Possible values : 0.0 to 1.0 (percentage).
preset_strength = 0.5

  ; When in 'curve' preset mode, this is the shape (slope) of the curve.
  ; Possible values : -10.0 to 10.0
  ;   Negative values : The curve is logarithmic.
  ;   Zero : The curve is linear.
  ;   Positive values : The curve is exponential.
curve_preset_shape = 0.0

  ; The strength of the suspension pushback effect.
  ; When non zero, enables the suspension force effect.
  ; This will push on the trigger when your suspension compresses.
  ; Uses the suspension bias global setting.
  ; Possible values : 0.0 to 1.0 (percentage).
suspension_effect_strength = 0.0

  ; Smooths the suspension effect.
  ; This amplifies big changes and minimizes small changes.
  ; Possible values : true or false.
suspension_effect_smoothing = false

  ; The strength of the speed force effect.
  ; The faster you go, the harder it is to press on the trigger.
  ; Possible values : 0.0 to 1.0 (percentage).
speed_effect_strength = 0.5

[Throttle Settings]

  ; The simulation preset to use for this trigger.
  ; Possible values :
  ;   "constant"
  ;   "conventional_brakes"
  ;   "three_stage"
  ;   "curve"
preset = "constant"

  ; The overall average force applied to the trigger.
  ; The simulation will try to cap the force to this value,
  ; but environment effects may push it over.
  ; When in 'constant' preset mode, this is the constant force value.
  ; Possible values : 0.0 to 1.0 (percentage).
preset_strength = 0.001

  ; When in 'curve' preset mode, this is the shape (slope) of the curve.
  ; Possible values : -10.0 to 10.0
  ;   Negative values : The curve is logarithmic.
  ;   Zero : The curve is linear.
  ;   Positive values : The curve is exponential.
curve_preset_shape = 0.0

  ; The strength of the suspension pushback effect.
  ; When non zero, enables the suspension force effect.
  ; This will push on the trigger when your suspension compresses.
  ; Uses the suspension bias global setting.
  ; Possible values : 0.0 to 1.0 (percentage).
suspension_effect_strength = 0.25

  ; Smooths the suspension effect.
  ; This amplifies big changes and minimizes small changes.
  ; Possible values : true or false.
suspension_effect_smoothing = false

  ; The strength of the speed force effect.
  ; The faster you go, the harder it is to press on the trigger.
  ; Possible values : 0.0 to 1.0 (percentage).
speed_effect_strength = 0.0

```

## Todo
Just some notes so I don't forget. Assume none of this will ever happen.
- Expose settings through settings.ini.
- Port selection.
- Brake temp? What's the telemetry units.
