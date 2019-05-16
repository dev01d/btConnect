# What is this?

This fixes an how pulseaudio handles Bluethooth headphones and makes it function more like core audio (that has sane dafaults).

## PA's infuriating normal operation

When reconnecting Bluetooth headphones after they have been disconnected/powered off, pulseaudio does not automatically recognize them as a2dp and forces them to connect in HST mode (which includes mono audio -\_\_\_\_\_-).

> I created this repo for my own convenience/archiving and all code is from a [medium article](https://medium.com/@aiguofer/flawless-bluetooth-headset-mdr-100abn-on-linux-e745cb746671) that explains usage and how you too might be inconvenienced by pulseaudio's method of handling Bluetooth headphones on Linux.

### Side note

#### To make pulseaudio auto-select your headphones on connect

create `~/.config/pulse/default.pa` if it doesn't exist and then append

```ini
.include /etc/pulse/default.pa
load-module module-switch-on-connect
```

Afterwards restart pulseaudio to enable to changes

`pulseaudio -k && pulseaudio --start`

For the `switch_headset` command keyboard shortcut make sure to list the command as `bash ~/.local/bin/switch_headset`

#### File manifest:

```ini
├── 80-bt-headset.rules --> /etc/udev/rules.d/80-bt-headset.rules
├── a2dp-fix --> /usr/local/bin/a2dp-fix
├── a2dp-fix-wrapper --> /usr/local/bin/a2dp-fix-wrapper
└── switch_headset --> ~/.local/bin/switch_headset
```
