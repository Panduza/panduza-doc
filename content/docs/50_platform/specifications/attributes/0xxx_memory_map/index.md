







Design for max 50 registres (au dessus l'utilisateur devrait plutot couper sa map en plusieurs attributs)

Complexe Message memory map

--PROTOBUF--


| Field              | Type                 | Description             |
| ------------------ | -------------------- | ----------------------- |
| base_address       | uint64               | Base Address of the map |
| register_size      | enum (8, 16, 32, 64) |                         |
| number_of_register | uint64               |                         |
| rights             | enum (RO/RW)         |                         |
| values             | array of uint64      |                         |
| timestamps_ms      | array of uint64      |                         |





