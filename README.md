# lifeina-communication-protocol
## BLE
- Service: `0000fee9-0000-1000-8000-00805f9b34fb`
- Characteristic Notify: `d44bc439-abfd-45a2-b575-925416129601`
- Characteristic: `d44bc439-abfd-45a2-b575-925416129600`

## Read battery capacity
### Mobile terminal transmission
| Start Code     | Functon Code  | Data   | End Code |
| :------------: |:-------------:| :-----:| :-------:|
| 0xAA     | 0x8E | 0xFF | 0x55 |


### Box terminal reply
| Start Code     | Functon Code  | Data   | End Code |
| :------------: |:-------------:| :-----:| :-------:|
| 0xAA     | 0x8E | 0xXX | 0x55 |

- `0xXX`：Battery charge percentage and charging state

| Bit 7  | Bit 6  | Bit 5  | Bit 4  | Bit 3  | Bit 2  | Bit 1  | Bit 0 |
| :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----:|
| Charging state     | Battery capacity| - | - | - | - | - | - |


## Read historical temperature
### Mobile terminal transmission
### Box terminal reply