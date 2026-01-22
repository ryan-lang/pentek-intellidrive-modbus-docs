# PID10 - MOC Registers

The PID10 family exposes the following registers at Address 1 on the RS485 bus. Modbus registers are one-indexed, and
all registers are holding registers in the 4xxxx space.

Field names are a hybrid of official/unofficial sources, as well as community-generated names.

| ModbusRegister | FieldName                | TypeName | Flags | MinValue   | MaxValue   | DefaultValue | Notes                                             |
| -------------- | ------------------------ | -------- | ----- | ---------- | ---------- | ------------ | ------------------------------------------------- |
| 45001          |                          | FLOAT    | 0xC1  | 0.05       | 0.2        | 0.1225       |                                                   |
| 45003          |                          | FLOAT    | 0xC1  | 0.05       | 0.2        | 0.1057       |                                                   |
| 45005          |                          | FLOAT    | 0xC1  | 0.01       | 0.05       | 0.032        |                                                   |
| 45007          |                          | FLOAT    | 0xC1  | 0.01       | 0.05       | 0.0336       |                                                   |
| 45009          |                          | FLOAT    | 0xC1  | 0.01       | 0.05       | 0.0314       |                                                   |
| 45011          |                          | FLOAT    | 0xC1  | \-100      | 100        | 0.9          |                                                   |
| 45013          |                          | FLOAT    | 0xC1  | \-100      | 100        | 0.9          |                                                   |
| 45015          |                          | FLOAT    | 0xC1  | \-100      | 100        | 0            |                                                   |
| 45017          |                          | FLOAT    | 0xC1  | \-100      | 100        | 0            |                                                   |
| 45019          |                          | FLOAT    | 0xC1  | \-100      | 100        | 0.9          |                                                   |
| 45021          |                          | FLOAT    | 0xC1  | \-100      | 100        | 0.9          |                                                   |
| 45023          | UNIT_NUMBER              | UINT16   | 0xC9  | 887        | 892        | 887          |                                                   |
| 45101          | MOC_SOFTWARE_VERSION     | STRING20 | 0x01  | 0          | 127        | 0            | Version of the MOC software.                      |
| 45111          | MOC_CONFIG_VERSION       | STRING20 | 0x01  | 0          | 127        | 0            | Version of the persisted config (migrations?)     |
| 45131          |                          | BOOL     | 0x83  | 0          | 1          | 0            | Not copied to AOC                                 |
| 45132          |                          | BOOL     | 0x83  | 0          | 1          | 0            | Not copied to AOC                                 |
| 45133          |                          | BOOL     | 0x03  | 0          | 1          | 1            | Not copied to AOC                                 |
| 45134          |                          | UINT16   | 0x87  | 0          | 65535      | 0            | Not copied to AOC                                 |
| 45140          |                          | UINT16   | 0x07  | 0          | 65535      | 0            |                                                   |
| 45141          |                          | UINT32   | 0x01  | 0          | 4294967295 | 0            |                                                   |
| 45143          | MOC_ACTUAL_SPEED         | FLOAT    | 0x01  | FLOAT_MIN  | FLOAT_MAX  | 0            |                                                   |
| 45145          |                          | UINT16   | 0x07  | 0          | 65535      | 0            |                                                   |
| 45146          | MOTOR_SPEED_HZ           | FLOAT    | 0x07  | \-80       | 80         | 0            |                                                   |
| 45148          |                          | UINT16   | 0x07  | 0          | 65535      | 0            |                                                   |
| 45149          | MOC_MODBUS_INTERNAL_ADDR | UINT8    | 0x8B  | 1          | 247        | 1            | Internal address used for AOC -> MOC comms.       |
| 45150          | MOTOR_POWER_CONSUMPTION  | UINT32   | 0x01  | 0          | 4294967295 | 0            | Value in watts                                    |
| 45152          | MOTOR_PHASE_A_CURRENT    | FLOAT    | 0x01  | FLOAT_MIN  | FLOAT_MAX  | 0            | Value in amps                                     |
| 45154          | MOTOR_PHASE_B_CURRENT    | FLOAT    | 0x01  | FLOAT_MIN  | FLOAT_MAX  | 0            | Value in amps                                     |
| 45156          | MOTOR_PHASE_C_CURRENT    | FLOAT    | 0x01  | FLOAT_MIN  | FLOAT_MAX  | 0            | Value in amps                                     |
| 45158          | MOTOR_PHASE_VOLTAGE      | FLOAT    | 0x01  | FLOAT_MIN  | FLOAT_MAX  | 0            | Value in volts (unused?)                          |
| 45201          | MOTOR_SF_AMPS            | FLOAT    | 0x8B  | 0          | 18         | 0            | Value in amps                                     |
| 45203          | MOTOR_TYPE               | UINT16   | 0x8B  | 0          | 2          | 1            | 0 - 3 Phase, 1 - 1 Phase 2Wire, 2 - 1 Phase 3Wire |
| 45204          | SUPPLY_VOLTAGE           | UINT32   | 0x01  | 0          | 4294967295 | 0            | Value in volts                                    |
| 45206          | IGBT_TEMPERATURE         | FLOAT    | 0x01  | \-25       | 200        | 40           | Value in degrees Celsius                          |
| 45208          |                          | FLOAT    | 0x01  | 0          | 600        | 40           |                                                   |
| 45210          |                          | FLOAT    | 0x07  | 0          | 100        | 50           |                                                   |
| 45301          |                          | FLOAT    | 0x8B  | 200        | 800        | 480          |                                                   |
| 45303          |                          | FLOAT    | 0x8B  | 200        | 800        | 440          |                                                   |
| 45305          |                          | FLOAT    | 0x8B  | 200        | 800        | 250          |                                                   |
| 45307          |                          | FLOAT    | 0x8B  | 100        | 300        | 175          |                                                   |
| 45309          |                          | FLOAT    | 0x8B  | 100        | 300        | 190          |                                                   |
| 45311          |                          | FLOAT    | 0x8B  | 0          | 300        | 250          |                                                   |
| 45313          |                          | FLOAT    | 0x8B  | 75         | 110        | 90           |                                                   |
| 45315          | GROUND_FAULT_LIMIT       | UINT16   | 0x83  | 10         | 190        | 20           | Value in 0.1 amps                                 |
| 45401          |                          | FLOAT    | 0x8B  | 0          | 150        | 6            |                                                   |
| 45403          |                          | FLOAT    | 0x8B  | 0          | 150        | 15           |                                                   |
| 45405          |                          | FLOAT    | 0x8B  | 0          | 150        | 30           |                                                   |
| 45407          |                          | FLOAT    | 0x8B  | 0          | 150        | 60           |                                                   |
| 45409          |                          | FLOAT    | 0x8B  | 0          | 150        | 80           |                                                   |
| 45411          |                          | FLOAT    | 0x8B  | 0          | 300        | 10           |                                                   |
| 45413          |                          | FLOAT    | 0x8B  | 0          | 300        | 25           |                                                   |
| 45415          |                          | FLOAT    | 0x8B  | 0          | 300        | 57           |                                                   |
| 45417          |                          | FLOAT    | 0x8B  | 0          | 300        | 120          |                                                   |
| 45419          |                          | FLOAT    | 0x8B  | 0          | 300        | 230          |                                                   |
| 45421          |                          | FLOAT    | 0x8B  | 0          | 300        | 230          |                                                   |
| 45423          |                          | FLOAT    | 0x8B  | 0          | 300        | 10           |                                                   |
| 45425          |                          | FLOAT    | 0x8B  | 0          | 300        | 15           |                                                   |
| 45427          |                          | FLOAT    | 0x8B  | 0          | 300        | 74           |                                                   |
| 45429          |                          | FLOAT    | 0x8B  | 0          | 300        | 80           |                                                   |
| 45431          |                          | FLOAT    | 0x8B  | 0          | 300        | 185          |                                                   |
| 45433          |                          | FLOAT    | 0x8B  | 0          | 300        | 185          |                                                   |
| 45435          |                          | FLOAT    | 0x8B  | 0          | 300        | 22.5         |                                                   |
| 45437          |                          | FLOAT    | 0x8B  | 0          | 300        | 22.5         |                                                   |
| 45439          |                          | FLOAT    | 0x8B  | 0          | 300        | 82.5         |                                                   |
| 45441          |                          | FLOAT    | 0x8B  | 0          | 300        | 135          |                                                   |
| 45443          |                          | FLOAT    | 0x8B  | 0          | 0          | 250          |                                                   |
| 45445          |                          | FLOAT    | 0x8B  | 0          | 300        | 250          |                                                   |
| 45447          |                          | FLOAT    | 0x8B  | 0          | 300        | 15           |                                                   |
| 45449          |                          | FLOAT    | 0x8B  | 0          | 300        | 15           |                                                   |
| 45451          |                          | FLOAT    | 0x8B  | 0          | 300        | 55           |                                                   |
| 45453          |                          | FLOAT    | 0x8B  | 0          | 300        | 90           |                                                   |
| 45455          |                          | FLOAT    | 0x8B  | 0          | 300        | 230          |                                                   |
| 45457          |                          | FLOAT    | 0x8B  | 0          | 300        | 230          |                                                   |
| 45459          |                          | FLOAT    | 0x8B  | 0          | 3.1416     | 1.484        |                                                   |
| 45461          |                          | FLOAT    | 0x8B  | 0          | 3.1416     | 1.484        |                                                   |
| 45463          |                          | FLOAT    | 0x8B  | 0          | 3.1416     | 1.484        |                                                   |
| 45465          |                          | FLOAT    | 0x8B  | 0          | 3.1416     | 1.484        |                                                   |
| 45467          |                          | FLOAT    | 0x8B  | 0          | 3.1416     | 1.484        |                                                   |
| 45469          |                          | FLOAT    | 0x8B  | 0          | 3.1416     | 1.484        |                                                   |
| 45471          |                          | FLOAT    | 0x8B  | 0          | 150        | 125          |                                                   |
| 45473          |                          | FLOAT    | 0x8B  | 0          | 150        | 30           |                                                   |
| 45475          |                          | FLOAT    | 0x8B  | 0          | 300        | 100          |                                                   |
| 45477          |                          | FLOAT    | 0x8B  | 0          | 1          | 0.25         |                                                   |
| 45479          |                          | UINT16   | 0x8B  | 0          | 65535      | 40           |                                                   |
| 45480          |                          | UINT16   | 0x8B  | 0          | 10000      | 3600         |                                                   |
| 45500          | MOTOR_ABOVE_GROUND       | UINT16   | 0x8B  | 0          | 1          | 0            | 0 - Submersible, 1 - Above Ground                 |
| 45501          | RAMP_UP_TIME             | UINT16   | 0x8B  | 500        | 60000      | 2000         | Can only be set via backdoor.                     |
| 45502          | RAMP_DOWN_TIME           | UINT16   | 0x8B  | 500        | 60000      | 2000         | Can only be set via backdoor.                     |
| 45503          |                          | UINT16   | 0x8B  | 500        | 60000      | 10000        |                                                   |
| 45504          |                          | UINT16   | 0x8B  | 500        | 60000      | 10000        |                                                   |
| 45505          |                          | UINT16   | 0x8B  | 0          | 255        | 5            |                                                   |
| 45506          |                          | FLOAT    | 0x8B  | 0          | 1          | 0.002        |                                                   |
| 45508          |                          | UINT16   | 0x8B  | 0          | 65535      | 2400         |                                                   |
| 45509          |                          | UINT16   | 0x8B  | 0          | 50         | 16           |                                                   |
| 45510          |                          | UINT16   | 0x8B  | 1          | 5          | 3            |                                                   |
| 45511          |                          | UINT16   | 0x8B  | 0          | 1000       | 870          |                                                   |
| 45512          | SWITCHING_FREQUENCY      | UINT16   | 0x8B  | 4000       | 8000       | 8000         | Can only be set via backdoor. Value in Hz.        |
| 45513          | PID_RAMP_TIME            | UINT16   | 0x8B  | 500        | 60000      | 2000         | Can only be set via backdoor. Value in ms.        |
| 45601          |                          | UINT8    | 0x83  | 0          | 2          | 0            |                                                   |
| 45602          | GROUND_DETECTION_DISABLE | UINT8    | 0x03  | 0          | 1          | 1            |                                                   |
| 45603          |                          | UINT16   | 0x81  | 0          | 100        | 0            |                                                   |
| 45701          |                          | UINT16   | 0x83  | 30         | 80         | 30           | Not copied to AOC                                 |
| 45800          |                          | UINT32   | 0x01  | 0          | 4294967295 | 0            | Not copied to AOC                                 |
| 45901          |                          | UINT16   | 0x01  | 0          | 65535      | 0            | Not copied to AOC                                 |
| 45902          |                          | UINT16   | 0x07  | 0          | 20         | 0            | Not copied to AOC                                 |
| 45903          |                          | UINT16   | 0x07  | 0          | 65535      | 0            | Not copied to AOC                                 |
| 45904          |                          | INT32    | 0x07  | 0          | 0          | 0            | Not copied to AOC                                 |
| 45906          |                          | INT32    | 0x07  | 0          | 0          | 0            | Not copied to AOC                                 |
| 45908          |                          | INT32    | 0x07  | 0          | 0          | 0            | Not copied to AOC                                 |
| 45910          |                          | INT32    | 0x07  | 0          | 0          | 0            | Not copied to AOC                                 |
| 45912          |                          | UINT32   | 0x07  | 0          | 4294967295 | 0            | Not copied to AOC                                 |
| 45914          |                          | UINT32   | 0x07  | 0          | 4294967295 | 0            | Not copied to AOC                                 |
| 45916          |                          | FLOAT    | 0x07  | 0          | FLOAT_MAX  | 0            | Not copied to AOC                                 |
| 45930          |                          | INT32    | 0x07  | 0          | 0          | 0            |                                                   |
| 45932          |                          | INT32    | 0x07  | 0          | 0          | 0            |                                                   |
| 45934          |                          | INT32    | 0x07  | 0          | 0          | 0            |                                                   |
| 45936          |                          | INT32    | 0x07  | 0          | 0          | 0            |                                                   |
| 45938          |                          | INT32    | 0x87  | 0          | 19000      | 400          |                                                   |
| 45942          |                          | UINT16   | 0x87  | 0          | 65535      | 0            |                                                   |