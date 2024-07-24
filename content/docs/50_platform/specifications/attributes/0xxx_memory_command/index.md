interfaces registers ???








Complexe Message memory command
--PROTOBUF-- ?
- "": "w",
- "": 0,
- "": [42, 1, 2, 3],
- "": 500


--PROTOBUF--


| Field     | Type            | Description      |
| --------- | --------------- | ---------------- |
| cmd       | uint64          | Command to apply |
| index     | uint64          |                  |
| values    | array of uint64 |                  |
| repeat_ms | enum (RO/RW)    |                  |


```
message Test {
  repeated uint64 values = 1;
}
```

