---
title: "Neo Attributes"
weight: 1000
---




Attribute GENERIC
- tx
- rx



Attribute Info
    "type": "generic"
    "state": "run",
    "error": "error string",
    "attributes": [
        {
            "name": name
            "type": "volt"
        }
    ]


Attribute Boolean => payload 0 => false, 1 => true
Attribute String => 
Attribute Numeric => String avec nombre potentiellement en decimal





Attribute SI seulement pour faire de l'aquistion
    --- CMDS - decimal
    value
    --- ATTS - json 
    - value
    - SI: V, mV, pV, A, C/F, (unité à specifié de mani&re global pour tout panduza)



Attribute SI pour setter des valeurs
    --- CMDS - decimal
    value
    --- ATTS - json 
    - value
    - SI: V, mV, pV, A, C/F, (unité à specifié de mani&re global pour tout panduza)

    (si user want to change value)
    - min
    - max
    - decimal 



Attribute List of SI

array of value
SI



