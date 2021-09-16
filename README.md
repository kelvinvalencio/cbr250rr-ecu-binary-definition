# About CBR250RR ECU Binary Definition
### My personal project, aimed to analyze, publish, and improve CBR250RR stock ECU binary definition
Supported ECU Model is **38770-K64-N04**
I need your help to improve and categorize these maps!
You can help improving this definition by clicking **new issue** on **issues** tab OR **email me** kelvinvalencio@protonmail.com

## XDF Releases
I'm currently working hard to make an XDF. Publishing XDF soon...

## **Binary Definition**
### Ignition Map
- Identical maps are considered Cylinder 1 & Cylinder 2
- They haven't been grouped yet, **if you discover a pattern please contact me**
- I haven't found the correct factor offset, **if you know how to translate the numbers please contact me**
- Table size 25x35. Cell data size 2 Bytes (16 bit)

| Address | Name
| -- | --
| 0x45E5C | Ignition Timing I Cyl 1 |
| 0x46532 | Ignition Timing I Cyl 2 |
| 0x479B4 | Ignition Timing II Cyl 1 |
| 0x4808A | Ignition Timing II Cyl 2 |
| 0x4950C | Ignition Timing III Cyl 1 |
| 0x49BE2 | Ignition Timing III Cyl 2 |
| 0x4B064 | Ignition Timing IV Cyl 1 |
| 0x4B73A | Ignition Timing IV Cyl 2 |
| 0x4E84C | Ignition Timing V Cyl 1 |
| 0x4EF22 | Ignition Timing V Cyl 2 |

### Throttle-By-Wire Map
- There are 2 maps I don't know which riding mode it belongs, **contact me if you know!**
- I haven't found the correct factor offset, but the highest value of them all seem to be **13238**, **contact me if you know**
- Table size 25x35. Cell data size 2 Bytes (16 bit)

| Address | Name | Riding Mode
|-- | -- | --
|0x52CE8 | Throttle-By-Wire 5 | Sport+
|0x544B2 | Throttle-By-Wire 8 | Sport+
|0x55C7C | Throttle-By-Wire 11 | Sport+
|0x57446 | Throttle-By-Wire 14 | Sport+
|0x58C10 | Throttle-By-Wire 17 | Sport+
|0x5A3DA | Throttle-By-Wire 20 | Sport+
| - | - | -
|0x50D30 | Throttle-By-Wire 1 | (not sure)
|0x524FA | Throttle-By-Wire 4 | Sport
|0x53CC4 | Throttle-By-Wire 7 | Sport
|0x5548E | Throttle-By-Wire 10 | Sport
|0x56C58 | Throttle-By-Wire 13 | Sport
|0x58422 | Throttle-By-Wire 16 | Sport
|0x59BEC | Throttle-By-Wire 19 | Sport
| - | - | -
|0x5151E | Throttle-By-Wire 2 | (not sure)
|0x51D0C | Throttle-By-Wire 3 | Comfort
|0x534D6 | Throttle-By-Wire 6 | Comfort
|0x54CA0 | Throttle-By-Wire 9 | Comfort
|0x5646A | Throttle-By-Wire 12 | Comfort
|0x57C34 | Throttle-By-Wire 15 | Comfort
|0x593FE | Throttle-By-Wire 18 | Comfort
