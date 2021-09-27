# ℹ️ About CBR250RR ECU Binary Definition
This is my personal project, the goal is to analyze, publish, and improve CBR250RR stock ECU binary definition. <br>**This information wasn't publicly available on the Internet at the time of my first publication**, so my hope is that this project will be able to help individual/user/amateur tuners tune their own bike.  
Supported ECU Model is **38770-K64-N04**. Original bin checksum value: **C2FF** 

### Community Help & Support
I need your help to improve and categorize these maps! Discussions are encouraged here!
You can help improving this definition by clicking **new issue** in **issues** tab OR **email me at** <kelvinvalencio@protonmail.com>  
Your contributions will help me and others build a better definition. **I will credit your work** in the credits section.

### Warning
- I'm not responsible for any damage/consequences that occurs. This documentation is aimed to be a guide for individual/user/amateur tuners.
- Some if not all information published here might not be accurate or straight up incorrect, anything that you do with this information is entirely your responsibility, with that in mind, I very much accept corrections. If you find any inaccurate information, I will make sure to revise them.

# 📄 XDF Releases
### 👇XDF is now available for download👇<br>[CBR250RR 38770-K64-N04 XDF Release Download](https://github.com/kelvinvalencio/cbr250rr-ecu-binary-definition/releases/tag/v0.8)  
⚠️Please read the release note first before proceeding to flash or modify your binary


# 📑 Binary Definition
### Breakpoints
Value breakpoints, could be called axis data
- MAP units are still unknown, it could be actual pressure or just senso voltage, **contact me if you know**
- TPS highest value is 661, divided by 100 (percent) as 100% throttle input
- Cell data size 2 Bytes (16 bit)
- TBW breakpoint might not be accurate, I found it directly above TBW maps, highest value is 802

| Start Address | Description | Table Size | Conversion/Factor Offset
| -- | -- | -- | --
| 0x41222 | Manifold Air Pressure breakpoint | 25x1 | (not converted)
| 0x41254 | RPM breakpoint | 35x1 | (not converted)
| 0x411F0 | Throttle Position Sensor breakpoint | 25x1 | X/6.61
| 0x50CF6 | Throttle-By-Wire breakpoint | 29x1 | Unknown, please contact me if you know

### Fuel Map
Most likely injection duration in microseconds during intake stroke.
- Identical maps are considered Cylinder 1 & Cylinder 2 pair
- They haven't been grouped/categorized yet
- Unit for the values are unknown, **if you know please contact me**
- Table size 25x35. Cell data size 2 Bytes (16 bit)

| Start Address | Description | Conversion/Factor Offset
| -- | -- | --
| 0x4129A | Uncategorized Fuel 1 Cyl 1 | X/1000
| 0x41970 | Uncategorized Fuel 1 Cyl 2 | X/1000
| 0x42046 | Uncategorized Fuel 2 Cyl 1 | X/1000
| 0x4271C | Uncategorized Fuel 2 Cyl 2 | X/1000
| 0x42DF2 | Uncategorized Fuel 3 Cyl 1 | X/1000
| 0x434C8 | Uncategorized Fuel 3 Cyl 2 | X/1000
| 0x43B9E | Uncategorized Fuel 4 Cyl 1 | X/1000
| 0x44274 | Uncategorized Fuel 4 Cyl 2 | X/1000
| 0x50100 | Uncategorized Fuel 5 (no cyl pair found) | X/1000

### Start Of Injection
This map should specify injector timing/when to inject fuel in degrees before Top Dead Center during intake stroke.
- Table size is unknown, **if you know please contact me**
- Cell data size 1 Byte (8 bit)

| Start Address | Description | Conversion/Factor Offset
| -- | -- | --
| 0x4FF50 | Start Of Injection | Unknown, please contact me if you know

### Ignition Map
Ignition-related map. Most likely degrees before Top Dead Center to ignite spark plug during compression stroke.
- Identical maps are considered Cylinder 1 & Cylinder 2 pair
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

### Limiters
Thailand version of CBR250RR has RPM limiter of 15000. Their stock ECU's binary is compared to find useful limiter values

- These are not limiters by gear, still uncategorized, please let me know if you can group them
- Cell data size 2 Bytes (16 bit)

| Start Address | Columns | Description | Conversion/Factor Offset
| -- | -- | -- | --
| 0x44DD8 | 3 | RPM Limiter 1 | (not converted)
| 0x452A4 | 2 | RPM Limiter 2 | (not converted)
| 0x455F2 | 2 | RPM Limiter 3 | (not converted)
| 0x455FC | 2 | RPM Limiter 4 | (not converted)
| 0x45944 | 2 | RPM Limiter 5 | (not converted)
| 0x4594C | 1 | RPM Limiter 6 | (not converted)

### Throttle-By-Wire Map
This should specify actual throttle body opening (Throttle Input vs RPM vs Throttle Opening), though not confirmed yet. **Please test and send back the result to me**
- ⚠️There are 2 maps I don't know which riding mode they belong (TBW #1 & TBW #2), **contact me if you know!**
- This map might be categorized by gear, though not tested yet
- Factor offset is based on the highest value in these maps, which is **13238** divided by 100 (percent) as 100% throttle opening, **contact me if it's incorrect**
- Table size 29x35. Cell data size 2 Bytes (16 bit)

| Start Address | Description | Riding Mode | Conversion/Factor Offset
|-- | -- | -- | --
| 0x52CE8 | Uncategorized Throttle-By-Wire 5 | Sport+ | X/132.38
| 0x544B2 | Uncategorized Throttle-By-Wire 8 | Sport+ | X/132.38
| 0x55C7C | Uncategorized Throttle-By-Wire 11 | Sport+ | X/132.38
| 0x57446 | Uncategorized Throttle-By-Wire 14 | Sport+ | X/132.38
| 0x58C10 | Uncategorized Throttle-By-Wire 17 | Sport+ | X/132.38
| 0x5A3DA | Uncategorized Throttle-By-Wire 20 | Sport+ | X/132.38
|- | - | - | -
| 0x50D30 | Uncategorized Throttle-By-Wire 1 | (not sure) | X/132.38
| 0x524FA | Uncategorized Throttle-By-Wire 4 | Sport | X/132.38
| 0x53CC4 | Uncategorized Throttle-By-Wire 7 | Sport | X/132.38
| 0x5548E | Uncategorized Throttle-By-Wire 10 | Sport | X/132.38
| 0x56C58 | Uncategorized Throttle-By-Wire 13 | Sport | X/132.38
| 0x58422 | Uncategorized Throttle-By-Wire 16 | Sport | X/132.38
| 0x59BEC | Uncategorized Throttle-By-Wire 19 | Sport | X/132.38
|- | - | - | -
| 0x5151E | Uncategorized Throttle-By-Wire 2 | (not sure) | X/132.38
| 0x51D0C | Uncategorized Throttle-By-Wire 3 | Comfort | X/132.38
| 0x534D6 | Uncategorized Throttle-By-Wire 6 | Comfort | X/132.38
| 0x54CA0 | Uncategorized Throttle-By-Wire 9 | Comfort | X/132.38
| 0x5646A | Uncategorized Throttle-By-Wire 12 | Comfort | X/132.38
| 0x57C34 | Uncategorized Throttle-By-Wire 15 | Comfort | X/132.38
| 0x593FE | Uncategorized Throttle-By-Wire 18 | Comfort | X/132.38

# Tags
- CBR250RR Mapping / CBR250RR Map / CBR250RR XDF
- CBR250RR Stock ECU Binary Definition for Reflashing or Remapping
- CBR250RR Remapping Data
