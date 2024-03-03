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
  - Make sure the `dr2ds-settings.ini` file is next to `dr2ds.exe`.
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

## Settings.ini
You can customize the behavior through the `dr2ds-settings.ini` file. Most gamers have played around with ini files in the past, but if you haven't, worry not. It is well annotated with examples and everything.
```ini
todo
```

## Help
```
todo
```

## Todo
Just some notes so I don't forget. Assume none of this will ever happen.
- Expose settings through settings.ini.
- Port selection.
- Brake temp? What's the telemetry units.
