# About CBR250RR ECU Binary Definition
This is my personal project, the goal is to analyze, publish, and improve CBR250RR stock ECU binary definition. <br> My hope is that this project will be able to help individual/user/amateur tuners tune their own bike.  
Supported ECU Model is **38770-K64-N04**. Original bin checksum value: **C2FF** 

### Community Help & Support
I need your help to improve and categorize these maps!  
You can help improving this definition by clicking **new issue** in **issues** tab OR **email me** kelvinvalencio@protonmail.com  
Your contributions will help me and others build a better definition. **I will credit your work** in the credits section

### Warning
I'm not responsible for any damage/consequences that occurs. This documentation is aimed to be a guide for individual/user/amateur tuners

# XDF Releases
I'm currently working hard to make an XDF. Publishing XDF soon...

# Binary Definition
### Fuel Map
- Identical maps are considered Cylinder 1 & Cylinder 2
- They haven't been grouped/categorized yet
- Unit for the values are unknown, **if you know please contact me**
- Table size 25x35. Cell data size 2 Bytes (16 bit)

| Start Address | Description | Conversion/Factor Offset
| -- | -- | --
| 0x4129A | Uncategorized Fuel 1 Cyl 1 | Unknown, please contact me if you know
| 0x41970 | Uncategorized Fuel 1 Cyl 2 | Unknown, please contact me if you know
| 0x42046 | Uncategorized Fuel 2 Cyl 1 | Unknown, please contact me if you know
| 0x4271C | Uncategorized Fuel 2 Cyl 2 | Unknown, please contact me if you know
| 0x42DF2 | Uncategorized Fuel 3 Cyl 1 | Unknown, please contact me if you know
| 0x434C8 | Uncategorized Fuel 3 Cyl 2 | Unknown, please contact me if you know
| 0x43B9E | Uncategorized Fuel 4 Cyl 1 | Unknown, please contact me if you know
| 0x44274 | Uncategorized Fuel 4 Cyl 2 | Unknown, please contact me if you know
| 0x50100 | Uncategorized Fuel 5 (no cyl pair found) | Unknown, please contact me if you know

### Ignition Map
- Identical maps are considered Cylinder 1 & Cylinder 2
- They haven't been grouped/categorized yet, **if you discover a pattern please contact me**
- These maps could either be categorized by **gear** and **riding mode**, but not tested yet
- I haven't found the correct conversion/factor offset, **if you know how to translate the numbers please contact me**
- Table size 25x35. Cell data size 2 Bytes (16 bit)

| Start Address | Description | Conversion/Factor Offset
| -- | -- | --
| 0x45E5C | Uncategorized Ignition 1 Cyl 1 | Unknown, please contact me if you know
| 0x46532 | Uncategorized Ignition 1 Cyl 2 | Unknown, please contact me if you know
| 0x479B4 | Uncategorized Ignition 2 Cyl 1 | Unknown, please contact me if you know
| 0x4808A | Uncategorized Ignition 2 Cyl 2 | Unknown, please contact me if you know
| 0x4950C | Uncategorized Ignition 3 Cyl 1 | Unknown, please contact me if you know
| 0x49BE2 | Uncategorized Ignition 3 Cyl 2 | Unknown, please contact me if you know
| 0x4B064 | Uncategorized Ignition 4 Cyl 1 | Unknown, please contact me if you know
| 0x4B73A | Uncategorized Ignition 4 Cyl 2 | Unknown, please contact me if you know
| 0x4E84C | Uncategorized Ignition 5 Cyl 1 | Unknown, please contact me if you know
| 0x4EF22 | Uncategorized Ignition 5 Cyl 2 | Unknown, please contact me if you know

### Throttle-By-Wire Map
- There are 2 maps I don't know which riding mode they belong, **contact me if you know!**
- This map might be categorized by gear, not tested yet
- I haven't found the correct conversion/factor offset, but the highest value of them all seem to be **13238**, **contact me if you know**
- Table size 29x35. Cell data size 2 Bytes (16 bit)

| Start Address | Description | Riding Mode | Conversion/Factor Offset
|-- | -- | -- | --
|0x52CE8 | Uncategorized Throttle-By-Wire 5 | Sport+ | Unknown, please contact me if you know
|0x544B2 | Uncategorized Throttle-By-Wire 8 | Sport+ | Unknown, please contact me if you know
|0x55C7C | Uncategorized Throttle-By-Wire 11 | Sport+ | Unknown, please contact me if you know
|0x57446 | Uncategorized Throttle-By-Wire 14 | Sport+ | Unknown, please contact me if you know
|0x58C10 | Uncategorized Throttle-By-Wire 17 | Sport+ | Unknown, please contact me if you know
|0x5A3DA | Uncategorized Throttle-By-Wire 20 | Sport+ | Unknown, please contact me if you know
|- | - | - | -
|0x50D30 | Uncategorized Throttle-By-Wire 1 | (not sure) | Unknown, please contact me if you know
|0x524FA | Uncategorized Throttle-By-Wire 4 | Sport | Unknown, please contact me if you know
|0x53CC4 | Uncategorized Throttle-By-Wire 7 | Sport | Unknown, please contact me if you know
|0x5548E | Uncategorized Throttle-By-Wire 10 | Sport | Unknown, please contact me if you know
|0x56C58 | Uncategorized Throttle-By-Wire 13 | Sport | Unknown, please contact me if you know
|0x58422 | Uncategorized Throttle-By-Wire 16 | Sport | Unknown, please contact me if you know
|0x59BEC | Uncategorized Throttle-By-Wire 19 | Sport | Unknown, please contact me if you know
|- | - | - | -
|0x5151E | Uncategorized Throttle-By-Wire 2 | (not sure) | Unknown, please contact me if you know
|0x51D0C | Uncategorized Throttle-By-Wire 3 | Comfort | Unknown, please contact me if you know
|0x534D6 | Uncategorized Throttle-By-Wire 6 | Comfort | Unknown, please contact me if you know
|0x54CA0 | Uncategorized Throttle-By-Wire 9 | Comfort | Unknown, please contact me if you know
|0x5646A | Uncategorized Throttle-By-Wire 12 | Comfort | Unknown, please contact me if you know
|0x57C34 | Uncategorized Throttle-By-Wire 15 | Comfort | Unknown, please contact me if you know
|0x593FE | Uncategorized Throttle-By-Wire 18 | Comfort | Unknown, please contact me if you know
