






interfaces registers ???







Design for max 50 registres (au dessus l'utilisateur devrait plutot couper sa map en plusieurs attributs)

Complexe Message memory map
--PROTOBUF--
- base_address: 0,
- register_size: 8,
- number_of_register: 10
- rights (RO/RW)
- values
- last_read_timestamps_ms


Complexe Message memory command
--PROTOBUF-- ?
- "cmd": "w",
- "index": 0,
- "values": [42, 1, 2, 3],
- "repeat_ms": 500


