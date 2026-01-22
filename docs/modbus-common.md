# PID10 Modbus System

The PID10 exposes a Modbus RTU interface over its builtin RS485 port. By default, the communication parameters for this
serial interface are as follows:

| Parameter   | Value |
|-------------|-------|
| Baud Rate   | 19200 |
| Data Bits   | 8     |
| Parity Bits | None  |
| Stop Bits   | 1     |

| Device | Address |
|--------|---------|
| MOC    | 1       |
| AOC    | 2       |

These parameters may be changed via adjusting the appropriate registers in the AOC.

## Protocol Documentation

### Writing Registers, and Register Flags

It appears that most (all?) fields are writable by default, with specific exceptions. These are ultimately controlled
by the flags present in the parameter's metadata (see the register tables). These flags are not fully known, but appear
to be as below:

| Bit Index | Hex  | Purpose                    |
|-----------|------|----------------------------| 
| 1         | 0x01 | Readable over Modbus       |
| 2         | 0x02 | Writable when pump stopped |
| 3         | 0x04 | Writable when pump running |
| 4         | 0x08 | Persisted to EEPROM (?)    |
| 5         | 0x10 | Unknown                    |
| 6         | 0x20 | Unknown                    |
| 7         | 0x40 | Unknown                    |
| 8         | 0x80 | Persisted to Flash (?)     |

While certain parameters (e.g. `TRANSDUCER_CURRENT_VALUE`) are writable (????), writing to these values seems to have
no effect as the actual calculations are done against backend data in state. However, care is still advised - writing
to certain registers may have extremely unexpected results.

### Device Selection

The AOC is responsible for handling its own Modbus channel *and* communicating with the MOC. In other words, the MOC is
not directly connected to RS485 - all communication is handled by the AOC.

When a Modbus RTU request is sent to the MOC channel, it is buffered and sent to the MOC, which will respond in its own
time. This provides the most up-to-date information, but may cause delays if the MOC is otherwise busy.

If up-to-date values aren't required, integrators may read (cached) MOC values from the AOC. The register IDs between
the two devices are identical, with specific exceptions for values that aren't exposed (see the AOC register table).

### Error Codes

The PID10 will implement Exception Code 2 (`ILLEGAL_DATA_ADDRESS`) when a requested register ID is not accessible. If a
write were to fail due to an out-of-bounds error or if the device is in the wrong mode to handle a write, it will
instead report Exception Code 4 (`SERVER_FAILURE`). 