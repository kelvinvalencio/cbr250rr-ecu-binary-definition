# ℹ️ About CBR250RR ECU Binary Definition
CBR250RR Stock ECU's maps & other settings definition from its flash memory. The goal is to let CBR250RR MC51 owners tune their bikes using the well-known tuning software **TunerPro**.<br>
The following are known ECUs for CBR250RR MC51:
| Part No. | Region | Year/Type | Binary Available | XDF Available
| -- | -- | -- | -- | --
| 38770-K64-N04 | Indonesia | 2017-2019/Base and ABS Model | Yes | Yes
| 38770-K64-ND1 | Indonesia | 2020-2022/SP QS | Yes | Yes
| 38770-K64-N01 | Thailand | 2017-2019/Base and ABS Model | Yes | No
| 38770-K64-R01 | - | 2017-2019/HRC ECU | Yes | No

### Help
If you've tested the XDF, or know better about the conversion factor, map categorization, map figures, etc., you're welcome to suggest changes

### Warning
- If you decide to do anything with your ECU, I will not be responsible
- Assume nothing is reliable here, please test everything yourself and let me know the result

# 📄 XDF Releases for TunerPro
### XDF is in the <a href="https://github.com/kelvinvalencio/cbr250rr-ecu-binary-definition/releases" target="_blank">Releases</a> section <br>
![XDF Parameter Tree](https://i.imgur.com/eSzodMs.png)

# About ECU
- Produced by Keihin as one of Honda's ECU vendor, not much details about it
- Uses Renesas SH7058 32 bit microcontroller with SH-2E processor, SuperH (RISC) CPU Architecture developed by Hitachi and produced by Renesas
- Has 1 MB of flash memory, but only half occupied

# 📑 Binary Definition (N04)
### Axis Tables
- MAP 
- TPS highest value is 661, divided by 100 (percent) as 100% throttle opening(?)
- Cell data size 2 Bytes (16 bit)
- TBW axis might not be accurate, I found it directly above TBW maps, highest value is 802

| Start Address | Description | Columns | Conversion/Factor Offset
| -- | -- | -- | --
| 0x41222 | Manifold Air Pressure axis | 25 | (not converted)
| 0x41254 | RPM axis | 35 | (not converted)
| 0x411F0 | Throttle Position Sensor axis | 25 | X/6.61
| 0x50CF6 | Throttle-By-Wire axis | 29 | Unknown

### Fuel Map
Most likely injection duration in microseconds during intake stroke.
- Maps with similar values are considered Cylinder 1 & Cylinder 2 pair
- They haven't been grouped/categorized yet
- Unit for the values are unknown
- Cell data size 2 Bytes (16 bit)

| Start Address | Table Size |Description | Conversion/Factor Offset
| -- | -- | -- | --
| 0x4129A | 25x35 | Uncategorized Fuel 1 Cyl 1 | X/1000
| 0x41970 | 25x35 | Uncategorized Fuel 1 Cyl 2 | X/1000
| 0x42046 | 25x35 | Uncategorized Fuel 2 Cyl 1 | X/1000
| 0x4271C | 25x35 | Uncategorized Fuel 2 Cyl 2 | X/1000
| 0x42DF2 | 25x35 | Uncategorized Fuel 3 Cyl 1 | X/1000
| 0x434C8 | 25x35 | Uncategorized Fuel 3 Cyl 2 | X/1000
| 0x43B9E | 25x35 | Uncategorized Fuel 4 Cyl 1 | X/1000
| 0x44274 | 25x35 | Uncategorized Fuel 4 Cyl 2 | X/1000
| 0x50100 | 25x35 | Fuel 5 (Compensation > TPS v RPM) | X/1000
| 0x5AC2C | 25x1 | Balance IAP v TPS | Unknown

### Start Of Injection
This map should specify injector timing/when to inject fuel in degrees before Top Dead Center during intake stroke.
- Table size is unknown, **if you know please contact me**
- Cell data size 1 Byte (8 bit)

| Start Address | Description | Conversion/Factor Offset
| -- | -- | --
| 0x4FF50 | Start Of Injection | Unknown

### Ignition Map
Ignition-related map. Most likely degrees before Top Dead Center to ignite spark plug during compression stroke.
- Maps with similar values are considered Cylinder 1 & Cylinder 2 pair
- They haven't been grouped/categorized yet, **if you discover a pattern please contact me**
- Still in raw values, if you know the correct Conversion/Factor Offset, please let me know
- Table size 25x35. Cell data size 2 Bytes (16 bit)

| Start Address | Description | Conversion/Factor Offset
| -- | -- | --
| 0x45E5C | Uncategorized Ignition 1 Cyl 1 | Unknown
| 0x46532 | Uncategorized Ignition 1 Cyl 2 | Unknown
| 0x479B4 | Uncategorized Ignition 2 Cyl 1 | Unknown
| 0x4808A | Uncategorized Ignition 2 Cyl 2 | Unknown
| 0x4950C | Uncategorized Ignition 3 Cyl 1 | Unknown
| 0x49BE2 | Uncategorized Ignition 3 Cyl 2 | Unknown
| 0x4B064 | Uncategorized Ignition 4 Cyl 1 | Unknown
| 0x4B73A | Uncategorized Ignition 4 Cyl 2 | Unknown
| 0x4E84C | Uncategorized Ignition 5 Cyl 1 | Unknown
| 0x4EF22 | Uncategorized Ignition 5 Cyl 2 | Unknown

### Limiters
Thailand version of CBR250RR has RPM limiter of 15000. Their stock ECU's binary is compared to find useful limiter values

- These are not limiters by gear, still uncategorized, please let me know if you can group them
- Cell data size 2 Bytes (16 bit)

| Start Address | Columns | Description | Conversion/Factor Offset
| -- | -- | -- | --
| 0x44DD8 | 3 | Uncategorized RPM Limiter 1 | (not converted)
| 0x452A4 | 2 | Uncategorized RPM Limiter 2 | (not converted)
| 0x455F2 | 2 | Uncategorized RPM Limiter 3 | (not converted)
| 0x455FC | 2 | Uncategorized RPM Limiter 4 | (not converted)
| 0x45944 | 2 | Uncategorized RPM Limiter 5 | (not converted)
| 0x4594C | 1 | Uncategorized RPM Limiter 6 | (not converted)
| -- | -- | -- | --
| 0x5D92C | 2 | Speed Limiter 1 | X/90.09
| 0x5D928 | 1 | Speed Limiter 2 | X/90.09

### Throttle-By-Wire Map
This should specify actual throttle body opening (Throttle Input vs RPM vs Throttle Opening), though not confirmed yet. **Please test and send back the result to me**
- Factor offset is based on the highest value in these maps, which is **13238** divided by 100 for percentage display
- Table size 29x35. Cell data size 2 Bytes (16 bit)

| Start Address | Description | Transmission Gear | Riding Mode | Conversion/Factor Offset
|-- | -- | -- | -- | --
| 0x52CE8 | Throttle-By-Wire 5 | 1 | Sport+ | X/132.38
| 0x544B2 | Throttle-By-Wire 8 | 2 | Sport+ | X/132.38
| 0x55C7C | Throttle-By-Wire 11 | 3 | Sport+ | X/132.38
| 0x57446 | Throttle-By-Wire 14 | 4 | Sport+ | X/132.38
| 0x58C10 | Throttle-By-Wire 17 | 5 | Sport+ | X/132.38
| 0x5A3DA | Throttle-By-Wire 20 | 6 | Sport+ | X/132.38
|-- | -- | -- | -- | --
| 0x50D30 | Throttle-By-Wire 1 | 1 | (not tested yet) | X/132.38
| 0x524FA | Throttle-By-Wire 4 | Neutral/Clutch-In | (not tested yet) | X/132.38
| 0x53CC4 | Throttle-By-Wire 7 | 2 | Sport | X/132.38
| 0x5548E | Throttle-By-Wire 10 | 3 | Sport | X/132.38
| 0x56C58 | Throttle-By-Wire 13 | 4 | Sport | X/132.38
| 0x58422 | Throttle-By-Wire 16 | 5 | Sport | X/132.38
| 0x59BEC | Throttle-By-Wire 19 | 6 | Sport | X/132.38
|-- | -- | -- | -- | --
| 0x5151E | Throttle-By-Wire 2 | 1 | Comfort | X/132.38
| 0x51D0C | Throttle-By-Wire 3 | Neutral/Clutch-In | Comfort | X/132.38
| 0x534D6 | Throttle-By-Wire 6 | 2 | Comfort | X/132.38
| 0x54CA0 | Throttle-By-Wire 9 | 3 | Comfort | X/132.38
| 0x5646A | Throttle-By-Wire 12 | 4 | Comfort | X/132.38
| 0x57C34 | Throttle-By-Wire 15 | 5 | Comfort | X/132.38
| 0x593FE | Throttle-By-Wire 18 | 6 | Comfort | X/132.38

### Compensation
Compensation tables are looked up by the ECU as the final step to compensate some values before execution

| Start Address | Description | Table Size | Conversion/Factor Offset
| -- | -- | -- | --
| 0x4DA5C | Torque Limiter by Gear (probably limits the ignition timing) | 35x6 | Unknown
| 0x50100 | TPS v RPM | 25x35 | X/1000


### ECU Settings Switch/Flag
Toggle on/off for some ECU settings

| Address | Description | Bit Number to switch | LSB
| -- | -- | -- | --
| 0x500E4 | Enable Immobilizer | Bit 6 / 7th bit | No
| 0x500E4 | Enable AIS | Bit 15 / 16th bit | No
| 0x500E4 | Enable Decel Cut | Bit 9 / 10th bit | No
| 0x500E4 | Enable O2 Sensor | Bit 0 / 1st bit | No
| 0x500E4 | Enable O2 Sensor Heater | Bit 1 / 2nd bit | No
| 0x500EA | Disable Front Speed Sensor | Bit 10 | Yes

# Unsolved
- Conversion/Factor offset for [Ignition Map](#ignition-map)
- Gear in which Throttle-By-Wire 1 and Throttle-By-Wire 4 corresponds (See **[Throttle-By-Wire map](#throttle-by-wire-map)** section)
- All uncategorized RPM Limiters, which gear or mode each limiter belong to (See **[Limiters](#limiters)** section)
- [Ignition Map](#ignition-map) categorization & [Fuel Map](#fuel-map) categorization (gear, riding mode, etc.)
- Anything marked **Unknown**/**Uncategorized** in the definition

# Tags
- CBR250RR Mapping / CBR250RR Map / CBR250RR XDF
- CBR250RR Stock ECU Binary Definition for Reflashing or Remapping
- CBR250RR Reflashing / CBR250RR Remapping / CBR250RR Mapping Data
- 38770-K64-N04 XDF File / CBR250RR XDF
