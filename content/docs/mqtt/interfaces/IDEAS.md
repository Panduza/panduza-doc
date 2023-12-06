
--- devices
PC/Server
Adatpeur uart

--- interfaces
RELP
  - AT over UART
  - SCPI over UART or ETH
  - SHELL over SSH

ByteStream
  -

--- connecteur ?
SerialPort
SSH



REPL and ByteStream does not manage config of ssh or serialport
Maybe too complex for nothing ?
Maybe it could ease the tests for SerialPort with RELP too (like SCPI or AT)
useless ? just do SSH & SerialPort + manage REPL or Stream in client ?

# REPL

L’acronyme Read-Eval-Print-Loop désigne une interface dans laquelle on peut écrire une commande, l’exécuter, voir s’afficher une réponse et recommencer.
En programmation on parle souvent console et dans l’utilisation d’un système unix de shell ou d’interface en ligne de commande CLI.


# ByteStream

- data
  - tx
  - rx

- settings
  - state (opened/closed)
  - baudrate
  - ...

# Modbus

# Relay

# I2C

# SPI

# DIO

# AIO


