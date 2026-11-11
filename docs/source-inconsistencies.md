# Source inconsistencies and unresolved details

The report and presentation contain internal differences. This repository preserves them and does not choose an unsupported “correct” value. Confirm these against the actual prototype, notebooks and original team files before public release.

| Topic | Report | Presentation | Repository treatment |
|---|---|---|---|
| Project completion | Conclusion says 50% complete and discusses next-phase work | Claims 100% completion and successful dry/actual trials | Both claims recorded; not reconciled |
| LCD | 16×2 in block diagram and description | 20×4 in hardware list | Both listed; final installed display unknown |
| Keypad | 4×3 keypad described | 4×4 keypad listed | Both recorded; installed matrix unknown |
| Actuator | Block diagram/narrative: motor driver and 30 RPM DC motor; SG90 servo chapter also included | Hardware list includes servo motor | Exact final actuator arrangement unknown |
| IoT/cellular | ESP8266 in block diagram; GSM in narrative | GSM module in hardware list | Both are documented; interface/data flow unknown |
| Valve/flow | Solenoid valve and liquid flow sensor narrative | Grain-focused machine description | Liquid-flow passage may be generic/copied or may refer to an unclarified subsystem; not asserted as part of grain dispensing |
| Controller | ATmega328P named in block diagram and presentation; report contains unrelated AT89C52/LCD interfacing tutorial text | ATmega328P module | ATmega328P retained as intended main controller; AT89C52 tutorial is not treated as project implementation evidence |
| Load cell | 20 kg in block diagram; generic 5 kg load-cell tutorial also appears | 20 kg weight sensor | 20 kg is the stated project-level rating; generic 5 kg tutorial noted |
| Power transformer | Parts list: 14-0-14 V, 1 A; prose later says 12-0-12 V | Not specified | Secondary rating unresolved |
| RFID authorization | Report says match with code stored in database | Does not specify backend | Database location/storage mechanism unknown |

## Editorial treatment

The repository title and core concept are unchanged. Where the documents conflict, wording is qualified and the conflict is made visible. No undocumented pinout, source code, protocol, calibration value, result or component substitution has been invented.
