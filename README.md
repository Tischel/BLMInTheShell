# BLM in the Shell Plugin

A Final Fantasy XIV Dalamud Plugin that shows a [BLM in the Shell](https://miyehn.me/ffxiv-blm-rotation/) rotation in-game and in real time.

**This plugin is only meant to be used only as a practice tool!**<br>
**For this reason, this plugin will only work when attacking a Striking Dummy outside of a duty.**

![example](https://github.com/Tischel/BLMInTheShell/blob/master/example.gif)

## FAQ

**Q: How do I install it?**<br>
A: Once you have Dalamud setup you need to add `https://raw.githubusercontent.com/Tischel/BLMInTheShell/master/repo.json` to the list of Custom Plugin Repositories in the Experimental settings. Once this step is complete, the plugin should be visible in the plugin list and ready to be installed through it.

**Q: Does this plugin execute actions for me?**<br>
A: No!

**Q: Can I see the timeline while fighting the boss?**<br>
A: No! This is meant to be used as a practice tool and it doesn't work on duties.

**Q: Can I use this with other jobs?**<br>
A: Absolutely! However you will most likely need a tool that generates the files in the correct format (see below).

**Q: Can you share the code?**<br>
A: Probably not!

## Rotation Timeline

This plugin was designed to be used with timelines generated in [BLM in the Shell](https://miyehn.me/ffxiv-blm-rotation/).<br>
Simply create a rotation and export it in CSV format and then load it through the plugin in the Files tab.

### Format

The file should be a text file containing one action per line with the following format:<br>
`<time>,<action name/id>,<action type>,<cast time>`

| Data | Description | Type | Example |
| ----| ----------- | ------- | ------- |
| `time` | Amount of time in seconds since the combat started. Can be negative to account for countdown. | float | `1.337` |
| `action name` | Name of the action to display. Use `Tincture` for pot. | string | `Fire IV` |
| `action id` | ID of the action to display | int | `3577` |
| `action type` | Defines if the action is a GCD (`1`) or an oGCD (`0`). If this data is omitted the plugin will try to determine the type automatically. | int | `0` or `1` |
| `cast time` | Cast time for the action (0 for instant casts). | float | `2.48` |

### Example
```
time,action,isGCD,castTime
882,Swiftcast,0,0
882.7,Fire 3,1,0
883.4000000000001,Sharpcast,0,0
884.1000000000001,Ley Lines,0,0
885.1200000000002,Thunder 3,1,2.057
887.2770000000002,Fire 4,1,2.3035
889.6805000000002,Xenoglossy,1,0
890.3805000000002,Manafont,0,0
891.0805000000003,Amplifier,0,0
891.7805000000002,Fire 4,1,2.3035
894.1840000000002,Paradox,1,2.057
896.3410000000003,Fire 4,1,2.3035
898.7445000000004,Fire 4,1,2.3035
901.1480000000004,Fire 4,1,2.3035
903.5515000000004,Despair,1,2.4735
906.1250000000003,Xenoglossy,1,0
906.8250000000004,Triplecast,0,0
907.5250000000004,Transpose,0,0
908.2250000000005,Paradox,1,0
908.9250000000005,Lucid Dreaming,0,0
910.2820000000006,Xenoglossy,1,0
910.9820000000007,Sharpcast,0,0
912.3390000000007,Thunder 3,1,0
914.3960000000008,Fire 3,1,0
916.4530000000007,Fire 4,1,0
917.1530000000006,Addle,0,0
```

## Markers

This plugin is also capable of displaying the timeline markers that can be created in [BLM in the Shell](https://miyehn.me/ffxiv-blm-rotation/).<br>
To export the markers use the `Save marker tracks to file: [all tracks combined]` option in the website.
The generated file can then be loaded through the plugin in the Files tab.

### Format

The markers export is a json file with the following spec:

```
{
    "tracks": [
        {
            "markers": [
                "time": float (seconds since combat start),
                "duration": float (in seconds, if 0 the marker is displayed as a dot instead of a bar),
                "description": string,
                "color": string (in hex format, i.e #9755ef)
            ],
            ...
        },
        ...
    ]
}
```

