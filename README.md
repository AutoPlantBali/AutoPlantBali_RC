# AutoPlantBali RC
AutoPlantBali RC adalah remote control berbasis esp32 yang dikembangkan dari code sumber:
[RomanLut](https://github.com/RomanLut/hx_espnow_rc). Untuk Transmitter dan Receiver memiliki beberapa mode yang bisa digunakan.

## Transmitter AutoPlantBali RC
Transmitter AutoPlantBali adalah external module remote yang dapat menerima signal SBUS, PPM, stick PS2 dan remote control mobile apps (RemoteXY) via bluetooth.
* Fitur:
    - Support 16 Channel
    - Normal & Long Range Mode
    - Multiple Profile
    - Telemetry SPORT
    - Select Active Profile By CH16 
* Transmitter Wiring Diagram
* Configuration File
```text
PPM_MAX_CHANNEL=8
REMOTEXY_PROFILE=1
REMOTEXY_MODEL=1
REMOTEXY_THROTTLE_CENTER=0
REMOTEXY_ACCESS_PASSWORD=1234
REMOTEXY_SERIAL_SPEED=9600
ALARM_VBAT=0
MIN_ALARM_VBAT=35
```    
* Setup:
    * Radio
    * PS2 Controller
    * RemoteXY (Android and Ios)
* Profiles:
    - **Profile 1**
    ```json
    {
        "transmitter_mode" : "ESPNOW",
        "espnow_channel" : 3,
        "espnow_key" : 0,
        "espnow_long_range_mode" : false,
        "ap_name" : "hxrct",
        "ap_password" : ""
    }
    ```
    - **Profile 2**
    ```json
    {
        "transmitter_mode" : "ESPNOW",
        "espnow_channel" : 3,
        "espnow_key" : 0,
        "espnow_long_range_mode" : true,
        "ap_name" : "hxrct",
        "ap_password" : ""
    }
    ```
    - **Profile 3**
    ```json
    {
        "transmitter_mode": "XIROMINI",
        "ap_name": "XIRO_RC",
        "ap_password": "XIRO1234",
        "ap_channel": 3,
        "drone": "XPLORER_Mini_0b4a41",
        "drone_password": "XIRO1234"
    }
    ```
    - **Profile 4**
    ```json
    {
        "transmitter_mode": "BLEGAMEPAD"
    }
    ```
    - **Profile 5**
    ```json
    {
        "transmitter_mode": "KYFPV"
    }
    ```
    - **Profile 6**
    ```json
    {
        "transmitter_mode" : "ESPNOW",
        "espnow_channel" : 3,
        "espnow_key" : 0,
        "espnow_long_range_mode" : false,
        "ap_name" : "hxrct",
        "ap_password" : "",
        "packet_rate" : "MAX",
        "phy_rate" : "1M"
    }
    ```
    - **Profile 10 (Configuration Mode)**
    ```json
    {
        "transmitter_mode" : "CONFIG",
        "ap_name" : "hxrct",
        "ap_password" : "",
        "web_user" : "apb",
        "web_password" : "apb"
    }
    ```

## Receiver AutoPlantBali RC
* Receiver Wiring Diagram
* Configuration File
```text
VERSION=
DEVELOP=
WIFI_CHANNEL=3
KEY=0
WIFI_PASSWORD=12345678
LR_MODE=0
LOG_ACTIVE=0
SBUS_ACTIVE=1
RC_MODE=1
LOG_BAUDRATE=115200
ESC_CALIBRATION=0
UPDATE_FIRMWARE=0
```
* PWM Brushed
* Mode Receiver RC:
1.  **Mode 1 (RC Plane - Brushless)**

| CHANNEL         | SIGNAL      | KETERANGAN         |
|----------------:|------------:|-------------------:|
| CHANNEL 1       | Aileron     | Servo              |
| CHANNEL 2       | Elevator    | Servo              |
| CHANNEL 3       | Throttle    | ESC Brushless      |
| CHANNEL 4       | Rudder      | Servo              |

2.  **Mode 2 (RC Plane - Brushed)**

| CHANNEL         | SIGNAL      | KETERANGAN         |
|----------------:|------------:|-------------------:|
| CHANNEL 1       | Aileron     | Servo              |
| CHANNEL 2       | Elevator    | Servo              |
| CHANNEL 3       | Throttle    | PWM Brushed        |
| CHANNEL 4       | Rudder      | Servo              |

3.  **Mode 3 (RC Plane - 2 Channel Brushed)**

| CHANNEL         | SIGNAL      | KETERANGAN         |
|----------------:|------------:|-------------------:|
| CHANNEL 1       | Aileron     | Left PWM Brushed   |
| CHANNEL 2       | Elevator    | Left PWM Brushed   |
| CHANNEL 3       | Throttle    | Right PWM Brushed  |
| CHANNEL 4       | Rudder      | Right PWM Brushed  |

4.  **Mode 4 (RC Plane - Brushless Elevon Mixing)**

| CHANNEL         | SIGNAL      | KETERANGAN         |
|----------------:|------------:|-------------------:|
| CHANNEL 1       | Aileron     | Servo              |
| CHANNEL 2       | Elevator    | Servo              |
| CHANNEL 3       | Throttle    | ESC Brushless      |
| CHANNEL 4       | Throttle    | ESC Brushless      |

5.  **Mode 5 (RC Plane - Brushed Elevon Mixing)**

| CHANNEL         | SIGNAL      | KETERANGAN         |
|----------------:|------------:|-------------------:|
| CHANNEL 1       | Aileron     | Servo              |
| CHANNEL 2       | Elevator    | Servo              |
| CHANNEL 3       | Throttle    | PWM Brushed        |
| CHANNEL 4       | Throttle    | PWM Brushed        |

* Openlog
* SBUS Output Receiver
* Quadcopter Drone (MultiWii)

## Battery AutoPlantBali RC
