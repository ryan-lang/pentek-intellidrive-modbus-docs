# PID10 - AOC Registers

The PID10 family exposes the following registers at Address 2 on the RS485 bus. Modbus registers are one-indexed, and
all registers are holding registers in the 4xxxx space.

Field names are a hybrid of official/unofficial sources, as well as community-generated names. The Param# field is an
internal reference extracted from the VFD's firmware for UI or other purposes. It is here for completeness only.

| ModbusRegister | Param# | FieldName                | TypeName | Flags | MinValue     | MaxValue   | DefaultValue | Notes                                                                |
| -------------- | ------ | ------------------------ | -------- | ----- | ------------ | ---------- | ------------ | -------------------------------------------------------------------- |
| 40001          |        | AOC_SOFTWARE_VERSION     | STRING20 | 0x01  | 0            | 127        | 0            | Version of the AOC software.                                         |
| 40011          |        | AOC_CONFIG_VERSION       | STRING20 | 0x01  | 0            | 127        | 0            | Version of the persisted config (migrations?)                        |
| 40021          |        | BUILD_DATE               | STRING20 | 0x01  | 0            | 127        | 0            | Build date for AOC software.                                         |
| 40031          |        | FAULT_CODE               | UINT32   | 0x01  | 0            | 4294967295 | 0            | Bitfield.                                                            |
| 40033          |        |                          | UINT32   | 0x01  | 0            | 4294967295 | 0            |                                                                      |
| 40035          |        |                          | BOOL     | 0x83  | 0            | 1          | 0            |                                                                      |
| 40036          |        |                          | BOOL     | 0x83  | 0            | 1          | 0            |                                                                      |
| 40037          |        |                          | BOOL     | 0x03  | 0            | 1          | 0            |                                                                      |
| 40038          | 69     |                          | UINT16   | 0x83  | 0            | 65535      | 0            |                                                                      |
| 40039          |        |                          | BOOL     | 0x07  | 0            | 1          | 0            |                                                                      |
| 40040          |        |                          | UINT8    | 0x83  | 0            | 2          | 0            |                                                                      |
| 40041          | 110    | OPERATION_STATE          | UINT8    | 0x87  | 0            | 8          | 0            | Enum value. Writes not supported.                                    |
| 40042          | 111    | RUN_MODE                 | UINT8    | 0x87  | 0            | 3          | 0            | 0 - Stop, 1 - Pump Out, 2 - Auto. Writes not supported.              |
| 40043          | 0      |                          | BOOL     | 0x83  | 0            | 1          | 0            |                                                                      |
| 40044          | 1      |                          | BOOL     | 0x83  | 0            | 1          | 0            |                                                                      |
| 40045          |        | RS485_BAUD_RATE          | UINT8    | 0x8B  | 1            | 51         | 8            | Baudrate multiplier. 1 = 2400, 2= 4800, 4 = 9600, 8 = 19200, ...     |
| 40046          |        | RS485_PARITY_BIT         | UINT8    | 0x8B  | 0            | 2          | 0            | 0 - None, 1 - Even, 2 - Odd.                                         |
| 40047          |        | RS485_STOP_BITS          | UINT8    | 0x8B  | 1            | 2          | 1            | 1 - one stop bit, 2 - two stop bits                                  |
| 40048          |        | RS485_MODBUS_ADDR_AOC    | UINT8    | 0x8B  | 1            | 247        | 2            | Address for AOC on RS485 port.                                       |
| 40049          |        | RS485_MODBUS_ADDR_MOC    | UINT8    | 0x8B  | 1            | 247        | 1            | Address for MOC on RS485 port.                                       |
| 40050          |        |                          | UINT16   | 0x8B  | 0            | 10000      | 10           |                                                                      |
| 40051          | 76     | CLOCK_USE_24H            | BOOL     | 0x8F  | 0            | 1          | 0            |                                                                      |
| 40201          | 75     | SYSTEM_LANGUAGE          | UINT8    | 0x87  | 0            | 2          | 0            | 0 = English, 1 = French, 2 = Spanish                                 |
| 40202          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40203          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40204          | 60     | IO_INPUT1_ACTIVE         | BOOL     | 0x07  | 0            | 1          | 0            |                                                                      |
| 40205          | 61     | IO_INPUT2_ACTIVE         | BOOL     | 0x07  | 0            | 1          | 0            |                                                                      |
| 40206          | 62     | IO_OUTPUT_ACTIVE         | BOOL     | 0x07  | 0            | 1          | 0            | Apparently can toggle output freely. Neat!                           |
| 40207          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40208          | 59     |                          | BOOL     | 0x07  | 0            | 1          | 0            |                                                                      |
| 40209          | 82     | PID_PGAIN                | UINT16   | 0x83  | 0            | 10000      | 1500         |                                                                      |
| 40210          | 83     | PID_TINTEG               | UINT16   | 0x83  | 20           | 65000      | 1500         | Value in ms                                                          |
| 40211          | 84     | PID_TDERIV               | UINT16   | 0x83  | 0            | 10000      | 60           | Value in ms                                                          |
| 40212          | 85     | PID_DERIV_LIM            | UINT16   | 0x83  | 0            | 2000       | 120          |                                                                      |
| 40213          | 86     |                          | UINT16   | 0x83  | 20           | 10000      | 60           |                                                                      |
| 40214          | 98     | PUMPOUT_SPEED            | UINT16   | 0x87  | 30           | 80         | 45           |                                                                      |
| 40215          |        |                          | FLOAT    | 0x07  | 0            | 100000     | 0            |                                                                      |
| 40217          |        |                          | BOOL     | 0x07  | 0            | 1          | 0            |                                                                      |
| 40218          | 95     | PRESSURE_UNIT            | UINT16   | 0x8B  | 0            | 1          | 0            | 0 = PSI, 1 = kPa                                                     |
| 40219          | 97     | SETPOINT_INTERNAL        | UINT16   | 0x87  | 103          | 2068       | 414          | Value in kPa                                                         |
| 40220          | 112    |                          | UINT16   | 0x83  | 0            | 2068       | 0            |                                                                      |
| 40221          | 113    | TRANSDUCER_MAX_VALUE     | UINT16   | 0x83  | 689          | 2068       | 689          | Value in kPa                                                         |
| 40222          | 94     | TRANSDUCER_CURRENT_VALUE | UINT16   | 0x07  | 0            | 65535      | 0            | Value in kPa                                                         |
| 40223          | 79     |                          | UINT16   | 0x8F  | 0            | 65535      | 0            |                                                                      |
| 40224          | 80     | DRY_RUN_DETECTION_TIME   | UINT16   | 0x8F  | 5            | 600        | 15           | Value in seconds                                                     |
| 40225          | 77     | DRY_RUN_RESET_LIMIT      | UINT16   | 0x8F  | 0            | 5          | 3            |                                                                      |
| 40226          | 78     | DRY_RUN_RESET_DELAY      | UINT16   | 0x8F  | 3            | 60         | 10           | Value in seconds (?)                                                 |
| 40227          |        |                          | UINT8    | 0x07  | 0            | 1          | 0            |                                                                      |
| 40228          | 100    |                          | UINT16   | 0x87  | 0            | 1          | 0            |                                                                      |
| 40229          | 106    | DRY_RUN_FILLTIME         | UINT16   | 0x87  | 15           | 600        | 60           | Value in seconds                                                     |
| 40230          | 99     | SETPOINT_EXTERNAL        | UINT16   | 0x87  | 103          | 2068       | 276          | Value in kPa                                                         |
| 40231          | 101    | IO_INPUT1_FUNCTION       | UINT16   | 0x83  | 0            | 3          | 0            | 0 - Unused, 1 - RunEnable, 2 - ExternalFault, 3 - UseExtSetpoint     |
| 40232          | 102    | IO_INPUT2_FUNCTION       | UINT16   | 0x83  | 0            | 3          | 0            | 0 - Unused, 1 - RunEnable, 2 - ExternalFault, 3 - UseExtSetpoint     |
| 40233          | 3      |                          | UINT16   | 0x83  | 0            | 2500       | 1000         |                                                                      |
| 40234          | 89     | PUMP_FREQUENCY_MAX       | UINT16   | 0x83  | 30           | 80         | 60           |                                                                      |
| 40235          | 90     | PUMP_FREQUENCY_MIN       | UINT16   | 0x83  | 30           | 80         | 30           |                                                                      |
| 40236          | 128    |                          | UINT16   | 0x83  | 0            | 190        | 5            |                                                                      |
| 40237          | 109    | APP_PASSWORD             | UINT16   | 0x87  | 0            | 9999       | 7777         |                                                                      |
| 40238          | 107    |                          | UINT16   | 0x83  | 0            | 1          | 1            |                                                                      |
| 40239          | 108    | APP_PASSWORD_TIMEOUT     | UINT16   | 0x87  | 1            | 360        | 60           | Value in minutes.                                                    |
| 40240          | 123    | PIPE_BREAK_HOURS         | UINT16   | 0x87  | 1            | 100        | 24           |                                                                      |
| 40241          | 122    | PIPE_BREAK_ENABLED       | UINT16   | 0x87  | 0            | 1          | 0            |                                                                      |
| 40242          | 93     |                          | UINT16   | 0x83  | 0            | 4095       | 3121         |                                                                      |
| 40243          | 92     |                          | UINT16   | 0x83  | 0            | 4095       | 625          |                                                                      |
| 40244          | 91     |                          | UINT16   | 0x07  | 0            | 4095       | 0            |                                                                      |
| 40245          | 96     |                          | UINT16   | 0x83  | 0            | 2          | 1            |                                                                      |
| 40246          | 87     |                          | UINT16   | 0x83  | 0            | 2          | 0            |                                                                      |
| 40247          | 114    |                          | UINT16   | 0x07  | 0            | 65535      | 10           |                                                                      |
| 40248          | 115    |                          | UINT16   | 0x07  | 0            | 65535      | 6            |                                                                      |
| 40249          | 119    |                          | UINT16   | 0x83  | 103          | 2068       | 552          |                                                                      |
| 40250          | 118    | SLEEP_WAKEUP_DIFF        | UINT16   | 0x87  | 34           | 103        | 34           | Value in kPa                                                         |
| 40251          | 120    | SLEEP_WAKEUP_DELAY       | UINT16   | 0x87  | 3            | 120        | 15           | Value in seconds                                                     |
| 40252          | 117    | SLEEP_BOOST_DELAY        | UINT16   | 0x87  | 30           | 300        | 60           | Value in seconds                                                     |
| 40253          | 116    | SLEEP_BOOST_DIFF         | UINT16   | 0x87  | 21           | 69         | 21           |                                                                      |
| 40254          | 121    |                          | UINT16   | 0x83  | 3            | 30         | 3            |                                                                      |
| 40255          | 103    | IO_OUTPUT_FUNCTION       | UINT16   | 0x83  | 0            | 2          | 0            | 0 - Unused, 1 - Running, 2 - Fault                                   |
| 40256          | 125    |                          | UINT16   | 0x87  | 0            | 65535      | 0            |                                                                      |
| 40257          | 124    |                          | UINT16   | 0x87  | 0            | 65535      | 0            |                                                                      |
| 40258          | 134    | SETPOINT_OVERPRESSURE    | UINT16   | 0x8F  | 103          | 2068       | 552          | Value in kPa                                                         |
| 40259          | 81     | DRY_RUN_SENSITIVITY      | UINT16   | 0x8F  | 0            | 2068       | 68           |                                                                      |
| 40901          |        |                          | UINT16   | 0x01  | 0            | 65535      | 0            |                                                                      |
| 40902          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40903          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40904          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40905          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40906          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40907          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40908          |        |                          | UINT16   | 0x07  | 0            | 65535      | 0            |                                                                      |
| 40909          |        |                          | UINT32   | 0x01  | 0            | 4294967295 | 0            |                                                                      |
| 41000          |        | REMOTE_MOTOR_COMMAND     | UINT16   | 0x07  | 0            | 65535      | 0            | 1 - Auto Run, 2 - Stop. Resets to 0 after command processed.         |
| 42051          | 76     | CLOCK_USE_24H            | BOOL     | 0x8F  | 0            | 1          | 1            | Unused? Conditional based on a function that hardcode returns false. |
| 42218          | 95     | PRESSURE_UNIT            | UINT16   | 0x8B  | 0            | 1          | 1            | Unused? Conditional based on a function that hardcode returns false. |
| 42234          | 89     | PUMP_FREQ_MAX            | UINT16   | 0x83  | 30           | 80         | 50           | Unused? Conditional based on a function that hardcode returns false. |

## MOC Register Cloning

In addition to the above table, the AOC will mirror most registers from the MOC. These are accessible at the same
register indices as are present in the MOC.

The following IDs are not shared: `45131` - `45134`, and `45701` - `45916`.

## Special Considerations

### Connection Parameters

If connection parameters are updated, the VFD must be *fully restarted* for the new parameters to apply.

### Operation States and Run Modes

Operation State and Run Mode cannot be set directly. If set, the value will simply revert to the true value on the next
AOC update tick.

Instead, commands may be sent through the `REMOTE_MOTOR_COMMAND` register.

Operation states are as follows:

| Value | Description                         |
|-------|-------------------------------------|
|     0 | Motor Stopped                       |
|     1 | Auto Run Initializing               |
|     2 | Auto Run - Target Fixed Pressure    |
|     3 | Auto Run - Boosting Pressure        |
|     4 | Motor Sleeping (Pressure OK)        |
|     5 | Auto Run - Maintaining Pressure     |
|     6 | Manual Run (Pump Out Mode)          |
|     7 | Fault (?)                           |
|     8 | Fault Recovery (?)                  |
