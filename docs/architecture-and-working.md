# Architecture and working principle

## Architecture shown in the original block diagram

The report's Figure 3.1 places an **ATmega328P** microcontroller at the centre. The depicted interfaces are:

| Block | Direction shown | Documented role |
|---|---|---|
| 12-digit RFID card | Input | Carries the user identifier |
| EM18 RFID reader | Input | Reads the RFID card identifier |
| ESP8266 IoT module | Input/interface | IoT connectivity block; protocol/backend not specified |
| Alarm | Input/interface | Shown connected to controller; trigger logic not detailed |
| Keypad | Input | User menu/selection interaction |
| LCD 16×2 | Display | User, weight and status information described in report |
| Motor driver / 30 RPM motors | Output | Drives grain dispenser mechanism |
| Dispenser setup | Mechanical subsystem | Stores/releases grain |
| 20 kg load cell + HX711 | Feedback | Measures dispensed weight and provides signal to controller |
| Ultrasonic sensor | Sensor | Included in diagram; precise use not fully explained |

The figure is source material, not an electrically complete schematic. It does not provide pin numbers, voltage domains, connector labels or all driver circuitry.

## Conceptual operational sequence

1. RFID card is presented to the reader.
2. Unique card data is read and checked against an authorized identifier. The report mentions a database but does not identify where it resides or how it is synchronized.
3. The user chooses an action through the keypad. The report lists amount entry, ration, balance check and exit.
4. The microcontroller starts the motor-driven dispensing arrangement for the user's allocation.
5. The load cell senses the collected grain weight; HX711 interfaces the small sensor signal to the controller.
6. At the target quantity, the controller is described as stopping dispensing/closing the mechanism.
7. LCD status is displayed. GSM communication is described for transaction information to a government office and consumer.

## Boundaries and ambiguities

- The diagram names ESP8266; the prose separately describes GSM. Their roles and data path are not fully defined.
- The report narrative describes DC motor plus shaft for opening/closing a lid. A separate solenoid-valve passage discusses liquid flow and flow sensing; it is not clearly applicable to grain dispensing.
- Ultrasonic sensor appears in the block diagram, but the report does not establish its exact function in the grain workflow.
- No complete state diagram, timing values, control algorithm or wiring table is provided.
