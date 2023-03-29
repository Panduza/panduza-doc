# DIO PZA Through Modbus

## Coils
---
| OFFSET | REGISTER NAME |  SIZE   |
| :----: | :-----------: | :-----: |
|   0    |   DIRECTION   | 32 bits |

DESCRIPTION:  
This register hold the direction settings for all available DIOs. One bit for one DIO. A one means the DIO is set as an output, and 0 as an input.

LAYOUT:

|  31   |  30   |  29   |  28   |  27   |  26   |  25   |  24   |  23   |  22   |  21   |  20   |  19   |  18   |  17   |  16   |  15   |  14   |  13   |  12   |  11   |  10   |   9   |   8   |   7   |   6   |   5   |   4   |   3   |   2   |   1   |   0   |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| GP31  | GP30  | GP29   | GP28  | GP27  | GP26  | GP25  | GP24  | GP23  | GP22  | GP21  | GP20  | GP19  | GP18  | GP17  | GP16  | GP15  | GP14  | GP13  | GP12  | GP11  | GP10  |  GP9  |  GP8  |  GP7  |  GP6  |  GP5  |  GP4  |  GP3  |  GP2  | GP1 | GP0 |

---
| OFFSET | REGISTER NAME |  SIZE   |
| :----: | :-----------: | :-----: |
|   0    |     PULLS     | 32 bits |

DESCRIPTION:  
This register hold the pulls value for all available DIOs. One bit for one DIO. A 1 means the DIO is set in pull-up, and 0 as a pull-down. This register takes effect only if the corresponfing DIO is set as an input.

LAYOUT:

|  31   |  30   |  29   |  28   |  27   |  26   |  25   |  24   |  23   |  22   |  21   |  20   |  19   |  18   |  17   |  16   |  15   |  14   |  13   |  12   |  11   |  10   |   9   |   8   |   7   |   6   |   5   |   4   |   3   |   2   |   1   |   0   |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| GP31  | GP30  | GP29   | GP28  | GP27  | GP26  | GP25  | GP24  | GP23  | GP22  | GP21  | GP20  | GP19  | GP18  | GP17  | GP16  | GP15  | GP14  | GP13  | GP12  | GP11  | GP10  |  GP9  |  GP8  |  GP7  |  GP6  |  GP5  |  GP4  |  GP3  |  GP2  | GP1 | GP0 |

---
| OFFSET | REGISTER NAME |  SIZE   |
| :----: | :-----------: | :-----: |
|   0    | OUTPUT VALUES | 32 bits |

DESCRIPTION:
This register hold the output value for all available DIOs. One bit for one DIO. A 1 means the DIO is set to HIGH, and 0 set to LOW. This register takes effect only if the corresponding DIO is set as an output.

LAYOUT:

|  31   |  30   |  29   |  28   |  27   |  26   |  25   |  24   |  23   |  22   |  21   |  20   |  19   |  18   |  17   |  16   |  15   |  14   |  13   |  12   |  11   |  10   |   9   |   8   |   7   |   6   |   5   |   4   |   3   |   2   |   1   |   0   |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| GP31  | GP30  | GP29   | GP28  | GP27  | GP26  | GP25  | GP24  | GP23  | GP22  | GP21  | GP20  | GP19  | GP18  | GP17  | GP16  | GP15  | GP14  | GP13  | GP12  | GP11  | GP10  |  GP9  |  GP8  |  GP7  |  GP6  |  GP5  |  GP4  |  GP3  |  GP2  | GP1 | GP0 |

## Discret Input
---
| OFFSET | REGISTER NAME |  SIZE   |
| :----: | :-----------: | :-----: |
|   0    | INPUT VALUES  | 32 bits |

DESCRIPTION:  
This register hold the actual value for all avaliable DIOs. One bit for one DIO. A 1 means the DIO is set to HIGH, and 0 set to LOW. This register is used to read an input or to verify the value of an output.

LAYOUT:

|  31   |  30   |  29   |  28   |  27   |  26   |  25   |  24   |  23   |  22   |  21   |  20   |  19   |  18   |  17   |  16   |  15   |  14   |  13   |  12   |  11   |  10   |   9   |   8   |   7   |   6   |   5   |   4   |   3   |   2   |   1   |   0   |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| GP31  | GP30  | GP29   | GP28  | GP27  | GP26  | GP25  | GP24  | GP23  | GP22  | GP21  | GP20  | GP19  | GP18  | GP17  | GP16  | GP15  | GP14  | GP13  | GP12  | GP11  | GP10  |  GP9  |  GP8  |  GP7  |  GP6  |  GP5  |  GP4  |  GP3  |  GP2  | GP1 | GP0 |

## Input Registers
---
| OFFSET | REGISTER NAME |  SIZE   |
| :----: | :-----------: | :-----: |
|   0    |  IDENTIFIER   | 6 bytes |

DESCRIPTION:  
This register identify the adapter as a panduza DIO adapter by holding a read-only magic.

LAYOUT:

|   0   |   1   |   2   |   3   |   4   |   5   |
| :---: | :---: | :---: | :---: | :---: | :---: |
|   P   |   Z   |   A   |   D   |   I   |   O   |

---
| OFFSET | REGISTER NAME |  SIZE  |
| :----: | :-----------: | :----: |
|   6    |      IOS      | 1 byte |

DESCRIPTION:  
This register hold the number of available DIOs provided by the adapter.

LAYOUT:

|   0   |
| :---: |
|  IOS  |

---
| OFFSET |  REGISTER NAME  |  SIZE   |
| :----: | :-------------: | :-----: |
|   7    | DIO ACCESS MASK | 4 bytes |

DESCRIPTION:  
This register hold the mask of read/write access for available DIOs. One bit for one DIO.

LAYOUT:

|     0     |     1      |      2      |      3      |
| :-------: | :--------: | :---------: | :---------: |
| mask[0:7] | mask[8:15] | mask[16:23] | mask[24:31] |

