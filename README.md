# HiHue (or HighlightHue)
Preview the color under the cursor with a hue light

## Installation
Make sure that `phue` is installed, if not
```
pip install --user phue
```
Then add the plugin to your vimrc; here shown for Vundle
```vimscript
Plugin 'offdroid/vim-hi-hue'
```
and install with `:PluginInstall` or equivalent of your plugin manager.

Next we need to connect to the bridge.
It is possible to configure your Hue bridge via variables, otherwise you need to specify them at runtime as arguments of the following command
```
:HiHueConnect <ip> <light_name>
```
This command has to be run at least once to pair/register the bridge.
When registering a new bridge make sure to _press the button before_ running `:HiHueConnect`.
If HiHue is not disabled at start it will auto-connect the next time.

## Configuration

### Options
```vimscript
let g:hiHue#disableAtStart = 0
let g:hiHue#bridgeIp = '192.168.1.2'
let g:hiHue#lightName = 'My light'
let g:hiHue#fallbackIfNotOverColor = 1
let g:hiHue#fallbackColor = '#000000'
let g:hiHue#maxBrightness = 1.0
let g:hiHue#minBrightness = 0.0
```

### Commands

Currently, implemented commands:
```
HiHueConnect
HiHueConnect <ip> <lightname>
HiHueDisconnect
HiHueDeregister
HiHueStatus
```

## Limitations
- Only RGB hex values starting with # are supported. The hexcode must be surrounded by whitespaces
- Only one Philips Hue light, specified by its name can be selected as an output
- Implementation is not asynchronous. Performance may be slow when rapidly moving between colors
