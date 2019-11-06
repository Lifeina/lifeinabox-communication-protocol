<img src="https://user-images.githubusercontent.com/7486270/68227716-7f0a5f00-fff4-11e9-9445-4da91872afa4.jpg" />

# lifeinabox-communication-protocol
## BLE
- Service: `0000fee9-0000-1000-8000-00805f9b34fb`
- Characteristic Notify: `d44bc439-abfd-45a2-b575-925416129601`
- Characteristic: `d44bc439-abfd-45a2-b575-925416129600`

## Read battery capacity
### Mobile terminal transmission
| Start Code     | Function Code  | Data   | End Code |
| :------------: |:-------------:| :-----:| :-------:|
| 0xAA     | 0x8E | 0xFF | 0x55 |


### Box terminal reply
| Start Code     | Function Code  | Data   | End Code |
| :------------: |:-------------:| :-----:| :-------:|
| 0xAA     | 0x8E | 0xXX | 0x55 |

- `0xXX`：Battery charge percentage and charging state

| Bit 7  | Bit 6  | Bit 5  | Bit 4  | Bit 3  | Bit 2  | Bit 1  | Bit 0 |
| :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----:|
| Charging state     | Battery capacity| Battery capacity | Battery capacity | Battery capacity | Battery capacity | Battery capacity | Battery capacity |
- Charging state values:
  - `0`: Discharged
  - `1`: In charge

- Battery capacity:
  - Value Range at not charging status: `0000001~0100100`
  - Value Range at charging status: `01000001~1100100`

## Read historical temperature
### Mobile terminal transmission
| Start Code     | Function Code  | Data   | End Code |
| :------------: |:-------------:| :-----:| :-------:|
| 0xAA     | 0x8E | 0xXX | 0x55 |

- `0xXX`: Past N hours
- Data range:
  - `0x06`: Past 6 hours
  - `0x12`: Past 12 hours
  - `0x18`: Past 24 hours
  - `0xF0`: Past 240 hours

### Box terminal reply
| Start Code     | Function Code  | Data lenght  | Data   | End Code |
| :------------: |:-------------:| :-----:| :-----:| :-------:|
| 0xAA     | 0x8E | 0xXX | 0x55 | 0xXX...0xXX | 0x55 |

- Data length `0xXX` Data range:
  - `0x06`: Data length 6 bytes, temperature in the last 6 hours
  - `0x12`: Data length 12 bytes, temperature in the last 12 hours
  - `0x18`: Data length 24 bytes, temperature in the last 24 hours
  - `0xF0`: Data length 240 bytes, temperature in the last 240 hours

- Data `0xXX…0xXX`：historical temperature Value Range: 0-255, means temperature range: 0-25.5℃.  Such as: 0x15 means 2.1℃
