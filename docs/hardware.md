# Hardware documentation

This inventory consolidates the hardware explicitly named across the report and presentation. Presence in a document does not prove that every item was installed in the final prototype. Differences are listed in `source-inconsistencies.md`.

| Component | Role described in the materials | Evidence / qualification |
|---|---|---|
| ATmega328P module | Main AVR microcontroller; coordinates interfaces and control | Central controller in block diagram and presentation list |
| RFID card (12-digit) | User identification token | Block diagram; report explains unique tag code |
| EM18 RFID reader | Reads RFID tag identifier | Named in report and block diagram |
| ESP8266 | IoT connectivity interface | Block diagram; details not provided |
| GSM module | Sends distribution information to consumer/government office | Report narrative and presentation list; exact model absent |
| LCD | Displays welcome/user/weight/quantity/balance/status | Report says 16×2; presentation lists 20×4 |
| Keypad | Menu and user input | Report says 4×3; presentation says 4×4 |
| Load cell, 20 kg | Measures dispensed material weight | Block diagram and presentation list |
| HX711 | Load-cell signal conditioning/24-bit ADC interface | Report description |
| DC motor, 30 RPM + motor driver | Operates dispenser mechanism | Block diagram and report |
| Servo motor (Tower Pro SG90) | Described as positional actuator; component chapter includes specifications | Report component chapter; presentation list |
| 5 V single-channel relay | Switching/control element | Presentation hardware list |
| Ultrasonic sensor | Additional sensing block | Block diagram; purpose not fully described |
| Alarm | Alarm block | Block diagram; logic not described |
| Solenoid valve | Described in report as liquid-flow control | Grain-specific applicability unclear; flagged as inconsistency |

## Load-cell measurement chain

The report describes the load cell as a force-to-electrical-signal transducer. HX711 is described as a precision 24-bit ADC with programmable gain, intended for load-cell/scale applications. The report's intended chain is **load cell → HX711 → microcontroller**. It mentions a 20 kg load cell in the block diagram/presentation and also includes generic 5 kg load-cell tutorial text; the installed rating should be verified against the actual hardware.

## Power supply described in the report

The report describes regulated +5 V and +12 V outputs. Its parts list includes 7812 and 7805 regulator ICs, 1N4007 diodes, 1000 µF/25 V electrolytic capacitor, 0.1 µF ceramic capacitors and a centre-tapped transformer. It describes a 230 V AC primary and gives differing secondary ratings in different passages. See `source-inconsistencies.md`.

**Safety:** The report discusses mains-powered circuits and ferric-chloride PCB etching. This repository is documentation, not a safe construction procedure. Work involving mains voltage, chemical etching, drilling or soldering requires qualified supervision, appropriate PPE and local safety procedures.
