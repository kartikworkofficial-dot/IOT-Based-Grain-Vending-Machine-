# Design & Development of IoT Based Grain Vending Machine

> **Academic project | B.Tech Mechatronics Engineering | Project Phase I report (2023–2024)**

This repository documents the project described in the supplied Phase I report and presentation. It is an academic prototype concept for automated ration/grain distribution in the context of India's Public Distribution System (PDS), using RFID-based user identification, a microcontroller, weight sensing and a motor-driven dispensing arrangement.

**Evidence boundary:** The supplied materials contain a Phase I report and presentation, but no firmware/source-code files, complete pin-level wiring schematic, bill of materials for the full machine, calibration records, test logs, or clear photographs of the assembled prototype. Accordingly, this repository documents the design and claims made in those materials; it does not invent missing implementation details or claim independent verification. The report's own conclusion says 50% completion, while the presentation claims 100% completion and successful trials. This discrepancy is recorded in [Source inconsistencies](docs/source-inconsistencies.md).

## Abstract

The project proposes an automated ration material distribution system intended to address issues described in the report's discussion of conventional ration shops, including possible inaccuracies in manually measured quantities and lack of transparency around uncollected allocations. RFID cards are used as an alternative means of user identification. The block diagram places an ATmega328P microcontroller at the centre, connected to an EM18 RFID reader and 12-digit RFID card, ESP8266 IoT module, alarm and keypad, with an LCD, motor-driver/30 RPM motor arrangement, ultrasonic sensor, dispenser setup, 20 kg load cell and HX711. The report also describes GSM communication, a regulated power supply, and a grain-weight feedback process. Exact implementation details are not fully consistent across the report and presentation and are therefore flagged rather than silently reconciled.

## Problem statement

The report identifies two concerns in the conventional ration distribution process: the possibility of inaccurate weighing due to human error, and the possibility that uncollected monthly material may be sold to others without the intended consumer's or government's knowledge. The proposed system aims to automate identification and dispensing and to improve traceability.

## Objectives stated in the presentation

- Design and develop the circuit for the system.
- Implement RFID card and reader functionality for user access.
- Build a basic structure and interface a load cell and HX711 amplifier with the ATmega microcontroller.
- Install a storage container for grains.
- Install a DC motor and gear for grain dispensing.
- Set dispensing time according to the volume/quantity of grains.

## Hardware components

The presentation's hardware list names: ATmega328P module, 20×4 LCD, RFID reader and cards, GSM module, HX711 module, 20 kg weight sensor, 5 V single-channel relay, ultrasonic sensor, servo motor and 4×4 keypad. The report additionally describes an EM18 RFID reader, 12-digit RFID card, ESP8266 IoT module, alarm, keypad, 16×2 LCD, 20 kg load cell, HX711, motor driver and 30 RPM DC motor, a servo motor (SG90 section), solenoid valve in the system narrative, and a +5 V/+12 V regulated supply. These are documented as reported, not as a verified final as-built bill of materials. See [Hardware](docs/hardware.md).

## Software and technologies

The materials identify the ATmega328P/AVR microcontroller, RFID identification, ESP8266 IoT connectivity, GSM communication, HX711 load-cell interface, LCD and keypad interface. They do **not** provide the actual firmware, programming language/version, IDE project, IoT protocol, cloud/database endpoint, GSM model, pin map, or complete software configuration. No software setup or flashing command can therefore be truthfully specified. See [Software and firmware status](docs/software.md).

## System architecture

The original report's block diagram is reproduced in [`diagrams/system-block-diagram.png`](diagrams/system-block-diagram.png). It shows:

- Inputs to the ATmega328P: RFID card/EM18 reader, ESP8266 IoT module, alarm and keypad.
- Display interface: LCD 16×2.
- Actuation/dispensing path: motor driver and 30 RPM motors to dispenser setup.
- Feedback/measurement: 20 kg load cell through HX711.
- Additional sensing: ultrasonic sensor.

The presentation lists a 20×4 LCD and some differing hardware items. The report's narrative also mentions GSM and a solenoid valve, which are not represented clearly in the block diagram. The exact final architecture and interconnections are not established by the supplied material.

## Working principle described in the report

1. A user presents an RFID card/tag to the EM18 RFID reader.
2. The reader obtains the card's unique identifier. The report describes comparing the identifier with an authorized code stored in a database; the location and implementation of that database are not specified.
3. Once the card is accepted, the ration distribution process is initiated according to the quantity associated with the user.
4. A DC motor and connected shaft are described as opening the container lid. The report says the motor subsequently rotates in the opposite direction to close it after a load-cell signal.
5. The load cell measures the dispensed material. The HX711 amplifies/converts the small load-cell signal for the microcontroller. The described control response is to stop/close dispensing when the target weight is reached.
6. The LCD is described as displaying welcome/user details, grain weight, liquid quantity and card balance. The keypad is described as providing menu choices including amount entry, ration, balance check and exit.
7. GSM is described as sending distribution information to a government office and consumer. The block diagram separately includes an ESP8266 IoT module; the actual network/backend implementation is not documented.

The report also includes a solenoid-valve/liquid-flow explanation. This appears inconsistent with the grain-only title and the motor-driven grain dispenser description; it is not treated here as a confirmed grain-dispensing subsystem.

## Power supply

The report describes a dual-output +5 V and +12 V regulated supply using a 230 V AC primary, 14-0-14 V / 1 A centre-tapped transformer (the text later also describes 12-0-12 V), two 1N4007 rectifier diodes, a 1000 µF / 25 V electrolytic capacitor, three 0.1 µF ceramic capacitors, a 7812 regulator and a 7805 regulator. It explains transformer step-down, full-wave rectification, smoothing and voltage regulation. The report's parts table and prose differ slightly on transformer secondary rating; consult [Source inconsistencies](docs/source-inconsistencies.md). Mains circuitry is hazardous and this document is not a build/safety certification.

## Diagrams and images

- [System block diagram](diagrams/system-block-diagram.png) — cropped from Figure 3.1 in the supplied report.
- [Presentation block diagram](diagrams/system-block-diagram-presentation.jpg) — extracted from the supplied presentation.

The supplied presentation's remaining visuals are primarily decorative/template graphics, not evidence of the assembled machine. No fabricated machine photographs or substitute diagrams are included.

## Installation and setup

There is no original firmware or software project in the supplied materials. Consequently, this repository cannot provide a reproducible firmware build, IDE configuration, library versions, pin assignments, network credentials, server setup, or flash procedure. The report mentions the HX711 library by Bogde as a resource, but does not provide a project-specific dependency manifest or firmware source. Do not infer that a working firmware image is available here.

## Operation

The conceptual user sequence described by the report is: scan authorized RFID card → select a menu/action using keypad → initiate the allocated grain dispensing → monitor weight via load cell/HX711 → stop the motor/close the dispenser at the target quantity → display status and (as described) communicate a transaction update. The precise state machine, card balance storage, quantity rules, error handling and network transaction flow are not supplied.

## Results and observations

The report contains a narrative describing a 50%-complete functional prototype with initial user testing. The presentation separately states that the project was 100% complete and that dry runs and actual grain-dispensing trials verified reliability. No numerical accuracy data, sample counts, calibration method, test cases, photographs of the final prototype, logs or measured results are supplied. These claims are preserved as source statements and are not independently validated. See [Testing and results](docs/testing-and-results.md).

## Applications described or implied

- Automated grain/ration dispensing at a Public Distribution System outlet.
- RFID-based beneficiary identification.
- Weight-based dispensing feedback.
- Potential transaction reporting to consumers and government offices (GSM/IoT communication is described, but backend details are absent).

## Limitations visible from the supplied materials

- Original source code and firmware are not supplied.
- Complete circuit schematic, pin map and wiring schedule are absent.
- IoT backend, database, protocol and security design are not documented.
- Calibration procedure and measured dispensing accuracy are absent.
- Report and presentation disagree on completion status and some components.
- No reliable as-built photographs or reproducible test evidence are supplied.

## Future scope stated in the presentation/report

1. Analyze consumer-interaction data to study consumption patterns, preferences and demand trends.
2. Develop a mobile application for availability checks, remote orders and collection notifications.
3. Integrate with government databases and systems for welfare programmes, subsidy distribution and citizen identification.

These are future proposals, not features claimed as implemented in this repository.

## Repository structure

```text
.
├── README.md
├── docs/
│   ├── architecture-and-working.md
│   ├── hardware.md
│   ├── software.md
│   ├── testing-and-results.md
│   ├── source-inconsistencies.md
│   ├── project-scope-and-future-work.md
│   └── source-materials-and-evidence.md
├── diagrams/
│   ├── system-block-diagram.png
│   └── system-block-diagram-presentation.jpg
├── hardware/README.md
├── software/README.md
├── src/README.md
├── tests/README.md
├── images/project/README.md
├── .gitignore
└── CONTRIBUTING.md
```

## Source and attribution

Documentation is derived from the supplied *Project Phase I Report* (2023–2024) and *MegaProject PPT* presentation. The original full academic report is intentionally not redistributed in this repository. Figure 3.1 is reproduced for project documentation. Confirm image/code ownership and obtain permission before publishing any additional third-party material.

## License

No license is included. The supplied materials do not establish the repository authors' chosen open-source license or rights to license all included material. Add a license only after the project owners agree on one.
