<!--
author:   Yannik Höll

email:    labruzzler@gmail.com

version:  0.0.1

language: en

narrator: US English Female

script:   https://tilk.github.io/digitaljs/main.js

@DigiSim
<script>
const div = document.getElementById("paper");

const json = JSON.parse(`@0`);

const circuit = new digitaljs.Circuit(json);
const paper = circuit.displayOn(div);
circuit.start();
</script>

<div id="paper">Test</div>
@end

dark: false
-->

# DigiSim for LiaScript

Implementation of DigitalJs for Liascript
[DigitalJS Source](https://github.com/tilk/digitaljs)


## Test Circuit

``` json @DigiSim
{
    "devices": {
        "dev0": {
            "celltype": "$button",
            "label": "a",
            "net": "a",
            "order": 0,
            "bits": 1
        },
        "dev1": {
            "celltype": "$button",
            "label": "b",
            "net": "b",
            "order": 1,
            "bits": 1
        },
        "dev2": {
            "celltype": "$button",
            "label": "d",
            "net": "d",
            "order": 2,
            "bits": 1
        },
        "dev3": {
            "celltype": "$lamp",
            "label": "o",
            "net": "o",
            "order": 3,
            "bits": 1
        },
        "dev4": {
            "celltype": "$lamp",
            "label": "c",
            "net": "c",
            "order": 4,
            "bits": 1
        },
        "dev5": {
            "label": "$or$tests/fulladder.sv:28$3",
            "celltype": "$or",
            "bits": 1
        },
        "dev6": {
            "label": "ha1",
            "celltype": "halfadder"
        },
        "dev7": {
            "label": "ha2",
            "celltype": "halfadder"
        }
    },
    "connectors": [
        {
            "to": {
                "id": "dev6",
                "port": "a"
            },
            "from": {
                "id": "dev0",
                "port": "out"
            },
            "name": "a"
        },
        {
            "to": {
                "id": "dev6",
                "port": "b"
            },
            "from": {
                "id": "dev1",
                "port": "out"
            },
            "name": "b"
        },
        {
            "to": {
                "id": "dev7",
                "port": "b"
            },
            "from": {
                "id": "dev2",
                "port": "out"
            },
            "name": "d"
        },
        {
            "to": {
                "id": "dev3",
                "port": "in"
            },
            "from": {
                "id": "dev7",
                "port": "o"
            },
            "name": "o"
        },
        {
            "to": {
                "id": "dev4",
                "port": "in"
            },
            "from": {
                "id": "dev5",
                "port": "out"
            },
            "name": "c"
        },
        {
            "to": {
                "id": "dev5",
                "port": "in1"
            },
            "from": {
                "id": "dev6",
                "port": "c"
            },
            "name": "c1"
        },
        {
            "to": {
                "id": "dev5",
                "port": "in2"
            },
            "from": {
                "id": "dev7",
                "port": "c"
            },
            "name": "c2"
        },
        {
            "to": {
                "id": "dev7",
                "port": "a"
            },
            "from": {
                "id": "dev6",
                "port": "o"
            },
            "name": "t"
        }
    ],
    "subcircuits": {
        "halfadder": {
            "devices": {
                "dev0": {
                    "celltype": "$input",
                    "label": "a",
                    "net": "a",
                    "order": 0,
                    "bits": 1
                },
                "dev1": {
                    "celltype": "$input",
                    "label": "b",
                    "net": "b",
                    "order": 1,
                    "bits": 1
                },
                "dev2": {
                    "celltype": "$output",
                    "label": "o",
                    "net": "o",
                    "order": 2,
                    "bits": 1
                },
                "dev3": {
                    "celltype": "$output",
                    "label": "c",
                    "net": "c",
                    "order": 3,
                    "bits": 1
                },
                "dev4": {
                    "label": "$and$tests/fulladder.sv:10$2",
                    "celltype": "$and",
                    "bits": 1
                },
                "dev5": {
                    "label": "$xor$tests/fulladder.sv:9$1",
                    "celltype": "$xor",
                    "bits": 1
                }
            },
            "connectors": [
                {
                    "to": {
                        "id": "dev4",
                        "port": "in1"
                    },
                    "from": {
                        "id": "dev0",
                        "port": "out"
                    },
                    "name": "a"
                },
                {
                    "to": {
                        "id": "dev5",
                        "port": "in1"
                    },
                    "from": {
                        "id": "dev0",
                        "port": "out"
                    },
                    "name": "a"
                },
                {
                    "to": {
                        "id": "dev4",
                        "port": "in2"
                    },
                    "from": {
                        "id": "dev1",
                        "port": "out"
                    },
                    "name": "b"
                },
                {
                    "to": {
                        "id": "dev5",
                        "port": "in2"
                    },
                    "from": {
                        "id": "dev1",
                        "port": "out"
                    },
                    "name": "b"
                },
                {
                    "to": {
                        "id": "dev2",
                        "port": "in"
                    },
                    "from": {
                        "id": "dev5",
                        "port": "out"
                    },
                    "name": "o"
                },
                {
                    "to": {
                        "id": "dev3",
                        "port": "in"
                    },
                    "from": {
                        "id": "dev4",
                        "port": "out"
                    },
                    "name": "c"
                }
            ]
        }
    }
}
```
