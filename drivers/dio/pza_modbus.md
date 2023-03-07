# DIO PZA Through Modbus


## Holding Regs


| Address | Description |
|---------|-------------|
|  0 & 1  | Magic  'P' 'Z' 'A' '!' / 0x50,...       |
|    2     | Mode  =1  for IO     |
|     3    |  Number of IO on the board           |

| 10 + X   |  direction de la pin (0=output, 1=input_pull_up, 2=input_pull_down, 3=input_open_drain)          |

X => numéro de la pin

## Coils

| 0 + X |  valeur de l'IO |

X => numéro de la pin

