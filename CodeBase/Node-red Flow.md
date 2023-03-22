```
[
    {
        "id": "352cad8ec24cc01d",
        "type": "tab",
        "label": "Motion Tracking Flow",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "c25876d4.ce1fc8",
        "type": "mqtt in",
        "z": "352cad8ec24cc01d",
        "name": "Acc_X",
        "topic": "XAcc",
        "qos": "0",
        "datatype": "utf8",
        "broker": "9ce35c9b.4536e",
        "nl": false,
        "rap": false,
        "inputs": 0,
        "x": 210,
        "y": 200,
        "wires": [
            [
                "7807f0c5.675a8"
            ]
        ]
    },
    {
        "id": "bbd8f925.e07018",
        "type": "mqtt in",
        "z": "352cad8ec24cc01d",
        "name": "Acc_Y",
        "topic": "YAcc",
        "qos": "0",
        "datatype": "utf8",
        "broker": "9ce35c9b.4536e",
        "nl": false,
        "rap": false,
        "inputs": 0,
        "x": 210,
        "y": 260,
        "wires": [
            [
                "7807f0c5.675a8"
            ]
        ]
    },
    {
        "id": "2126c6f5.54891a",
        "type": "mqtt in",
        "z": "352cad8ec24cc01d",
        "name": "Acc_Z",
        "topic": "ZAcc",
        "qos": "0",
        "datatype": "utf8",
        "broker": "9ce35c9b.4536e",
        "nl": false,
        "rap": false,
        "inputs": 0,
        "x": 210,
        "y": 320,
        "wires": [
            [
                "7807f0c5.675a8"
            ]
        ]
    },
    {
        "id": "5f5a8067.83228",
        "type": "mqtt in",
        "z": "352cad8ec24cc01d",
        "name": "Gyro_X",
        "topic": "XGyro",
        "qos": "0",
        "datatype": "utf8",
        "broker": "9ce35c9b.4536e",
        "nl": false,
        "rap": false,
        "inputs": 0,
        "x": 210,
        "y": 380,
        "wires": [
            [
                "7807f0c5.675a8"
            ]
        ]
    },
    {
        "id": "f69eac01.e78cd",
        "type": "mqtt in",
        "z": "352cad8ec24cc01d",
        "name": "Gyro_Y",
        "topic": "YGyro",
        "qos": "0",
        "datatype": "utf8",
        "broker": "9ce35c9b.4536e",
        "nl": false,
        "rap": false,
        "inputs": 0,
        "x": 210,
        "y": 440,
        "wires": [
            [
                "7807f0c5.675a8"
            ]
        ]
    },
    {
        "id": "184ce45e.7213ec",
        "type": "mqtt in",
        "z": "352cad8ec24cc01d",
        "name": "Gyro_Z",
        "topic": "ZGyro",
        "qos": "0",
        "datatype": "utf8",
        "broker": "9ce35c9b.4536e",
        "nl": false,
        "rap": false,
        "inputs": 0,
        "x": 210,
        "y": 500,
        "wires": [
            [
                "7807f0c5.675a8"
            ]
        ]
    },
    {
        "id": "7807f0c5.675a8",
        "type": "join",
        "z": "352cad8ec24cc01d",
        "name": "Join Sensor Data",
        "mode": "custom",
        "build": "object",
        "property": "payload",
        "propertyType": "msg",
        "key": "topic",
        "joiner": "\\n",
        "joinerType": "str",
        "accumulate": false,
        "timeout": "",
        "count": "6",
        "reduceRight": false,
        "reduceExp": "",
        "reduceInit": "",
        "reduceInitType": "",
        "reduceFixup": "",
        "x": 490,
        "y": 320,
        "wires": [
            [
                "401bbf9762a3396e",
                "3ba2cd7322c39ead"
            ]
        ]
    },
    {
        "id": "139ed9e49182e6a7",
        "type": "mysql",
        "z": "352cad8ec24cc01d",
        "mydb": "a4530ad6a18de60e",
        "name": "motiondb",
        "x": 960,
        "y": 320,
        "wires": [
            [
                "9811001508eb982d"
            ]
        ]
    },
    {
        "id": "401bbf9762a3396e",
        "type": "debug",
        "z": "352cad8ec24cc01d",
        "name": "debug 4",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 640,
        "y": 160,
        "wires": []
    },
    {
        "id": "9811001508eb982d",
        "type": "debug",
        "z": "352cad8ec24cc01d",
        "name": "debug 5",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 1120,
        "y": 320,
        "wires": []
    },
    {
        "id": "3ba2cd7322c39ead",
        "type": "function",
        "z": "352cad8ec24cc01d",
        "name": "insert sensor data into db",
        "func": "\nmsg.topic = \"INSERT INTO mpudata1(XAcc,YAcc,ZAcc,XGyro,YGyro,ZGyro) VALUES ('\" + msg.payload[\"XAcc\"] + \"','\" + msg.payload[\"YAcc\"] + \"','\" + msg.payload[\"ZAcc\"] + \"','\" + msg.payload[\"XGyro\"] + \"','\" + msg.payload[\"YGyro\"] + \"','\" + msg.payload[\"ZGyro\"] + \"')\";\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "initialize": "",
        "finalize": "",
        "libs": [],
        "x": 730,
        "y": 320,
        "wires": [
            [
                "44ec81cc9ce4acaa",
                "139ed9e49182e6a7"
            ]
        ]
    },
    {
        "id": "44ec81cc9ce4acaa",
        "type": "debug",
        "z": "352cad8ec24cc01d",
        "name": "debug 6",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 980,
        "y": 220,
        "wires": []
    },
    {
        "id": "9ce35c9b.4536e",
        "type": "mqtt-broker",
        "name": "",
        "broker": "192.168.8.154",
        "port": "1883",
        "clientid": "ESP32ClientSai",
        "autoConnect": true,
        "usetls": false,
        "protocolVersion": "4",
        "keepalive": "60",
        "cleansession": true,
        "birthTopic": "",
        "birthQos": "0",
        "birthPayload": "",
        "birthMsg": {},
        "closeTopic": "",
        "closeQos": "0",
        "closePayload": "",
        "closeMsg": {},
        "willTopic": "",
        "willQos": "0",
        "willPayload": "",
        "willMsg": {},
        "userProps": "",
        "sessionExpiry": "",
        "credentials": {}
    },
    {
        "id": "a4530ad6a18de60e",
        "type": "MySQLdatabase",
        "name": "motiondb",
        "host": "127.0.0.1",
        "port": "3306",
        "db": "motiondb",
        "tz": "",
        "charset": "UTF8"
    }
]
```
