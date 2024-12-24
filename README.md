# AutoPlantBali RC
AutoPlantBali RC adalah remote control berbasis esp32 yang dikembangkan dari code sumber:
[RomanLut](https://github.com/RomanLut/hx_espnow_rc). Untuk Transmitter dan Receiver memiliki beberapa mode yang bisa digunakan.

## Transmitter AutoPlantBali RC
Transmitter AutoPlantBali adalah external module remote yang dapat menerima signal SBUS, PPM, stick PS2 dan remote control mobile apps (RemoteXY) via bluetooth.

Marketplace: [Tokopedia](https://tokopedia.link/irYhezPOzPb)
* ### Fitur:
    - Support 16 Channel
    - Normal & Long Range Mode
    - Multiple Profile
    - Telemetry SPORT
    - Select Active Profile By CH16 
* ### Transmitter Wiring Diagram
  
  ![tx_diagram](/doc/image/TX/tx_diagram.png)
  
* ### Configuration File

| KEY                           | VALUE                             | KETERANGAN         |
|:------------------------------|:---------------------------------:|:-------------------|
| PPM_MAX_CHANNEL               | max 12, Default: 8                | Sesuikan dengan PPM out pada remote (channel terakhir akan menjadi channel 16 untuk config)|
| REMOTEXY_PROFILE              | 1 - 10, Default: 1                | Pilih profile untuk app REMOTEXY (Android / Ios)|
| REMOTEXY_MODEL                | 1 - 2, Default: 1                 | Pilih model/desain dari app REMOTEXY (Android / Ios)|
| REMOTEXY_THROTTLE_CENTER      | 1 or 0, Default: 0                | Pilih throttle center = 0 untuk rc plane atau 1 untuk rc car|
| REMOTEXY_ACCESS_PASSWORD      | 4 digit number, Default: 1234     | Password akses untuk membuka menu remote di app REMOTEXY (Android / Ios)|
| REMOTEXY_SERIAL_SPEED         | 9600 or 19200, Default: 9600      | Hubungkan module bluetooth HC-05 atau HM-10 untuk terhubung ke app REMOTEXY (Android / Ios)|
| ALARM_VBAT                    | 1 or 0, Default: 0                | Set 1 untuk mengaktifkan alarm low battery dan 0 untuk menonaktifkannya|
| MIN_ALARM_VBAT                | Volt Battery x 10, Default: 35    | Set volt per cell battery dikali 10, contoh: set 3.5Volt untuk aktifakan alarm maka valuenya 35|
| VBAT_OFFSET                   | Vbat offset value                 | Atur nilai offset vbat, contoh: battery 4V tapi di tampilan 3.5V, maka perlu atur nilai 0.5 agar sesuai dengan volt battery yaitu nilai offset 0.5 dikali 10 = 5|
| FLIP_DISPLAY                  | 1 or 0, Default: 0                | Set 1 untuk membalikan tampilan layar LCD 180 derajat|
   
* ### Setup:
    * ### Radio

      ![radio_pinout](/doc/image/TX/radio_pinout.png)

      ![tx_external_1](/doc/image/TX/tx_external_1.jpg)
      
      ![tx_external_2](/doc/image/TX/tx_external_2.jpg)
      
      ![tx_external_3](/doc/image/TX/tx_external_3.jpg)

      ### SBUS
      1. Create model selanjutnya pada tab External RF pilih SBUS.
         ![external_rf_sbus](/doc/image/TX/external_rf_sbus.jpg) 
      2. Pada tab mixes pilih CH16 lalu klik edit.
         ![tab_mixes](/doc/image/TX/tab_mixes.jpg)
         ![edit_mixes](/doc/image/TX/edit_mixes.jpg)
      3. Setting weight **0** dan offset sesuai profile yang ingin dipilih.

         - 1000...1100 ( or -100%) - profile 1
         - 1100...1200 ( or -80%)  - profile 2
         - 1200...1300 ( or -60%)  - profile 3
         - 1300...1400 ( or -40%)  - profile 4
         - 1400...1500 ( or -20%)  - profile 5
         - 1500...1600 ( or 0%)    - profile 6
         - 1600...1700 ( or +20%)  - profile 7
         - 1700...1800 ( or +40%)  - profile 8
         - 1800...1900 ( or +60%)  - profile 9
         - 1900...2000 ( or +80%)  - profile 10 (Configuration mode)

         ![mixes_ch16](/doc/image/TX/mixes_ch16.jpg)
         ![mixes_ch16_1](/doc/image/TX/mixes_ch16_1.jpg)    

      ### PPM
      1. Create model selanjutnya pada tab External RF pilih PPM. Default max ch range 8.
         ![external_rf_sbus](/doc/image/TX/external_rf_ppm.jpg) 
      2. Pada tab mixes pilih channel sesuai dengan max ch range lalu klik edit.
         ![tab_mixes](/doc/image/TX/tab_mixes.jpg)
         ![edit_mixes](/doc/image/TX/edit_mixes.jpg)
      3. Setting weight **0** dan offset sesuai profile yang ingin dipilih.

         - 1000...1100 ( or -100%) - profile 1
         - 1100...1200 ( or -80%)  - profile 2
         - 1200...1300 ( or -60%)  - profile 3
         - 1300...1400 ( or -40%)  - profile 4
         - 1400...1500 ( or -20%)  - profile 5
         - 1500...1600 ( or 0%)    - profile 6
         - 1600...1700 ( or +20%)  - profile 7
         - 1700...1800 ( or +40%)  - profile 8
         - 1800...1900 ( or +60%)  - profile 9
         - 1900...2000 ( or +80%)  - profile 10 (Configuration mode)

         ![mixes_ch16](/doc/image/TX/mixes_ch8.jpg)
         ![mixes_ch16_1](/doc/image/TX/mixes_ch8_1.jpg)   
  
    * ### PS2 Controller
      * ### PS2 Wiring

        | TX PIN          | PS2 PIN           |
        |:----------------|:------------------|
        | 3V3             | VCC               |
        | VSS             | GND               |
        | PS2_ATT         | CS (Attention)    |
        | PS2_CLK         | CLK (Clock)       |
        | PS2_CMD         | DO (Command)      |
        | PS2_DAT         | DI (Data)         |
      
        ![ps2_pinout](/doc/image/TX/ps2_pinout.png)
        ![ps2_button_info](/doc/image/TX/ps2_button_info.jpg)

      * ### Select Profile
        Untuk mengganti profile TX dengan cara tekan tombol **SELECT** pada PS2 Controller
      * ### Calibate Joystick
        Untuk melakukan kalibrasi joystick dengan cara masuk mode profile 10 (Config) lalu tekan tombol **START**, tunggu beberapa saat sampai proses kalibrasi selesai. Pada saat kalibrasi analog joystick tidak boleh digerakan atau dalam posisi center.

        ![ps2_controller_top](/doc/image/TX/ps2_controller_top.jpg)
        ![ps2_controller_bottom](/doc/image/TX/ps2_controller_bottom.jpg)
      
    * ### RemoteXY (Android and Ios)
      HC-05 Bluetooth Module  
      ![hc-05_module](/doc/image/TX/hc-05_module.png)

      HM-10 Bluetooth Module
      ![hm-10_module](/doc/image/TX/hm-10_module.jpg)

      | TX PIN          | HC-05 / HM-10 |
      |:----------------|:--------------|
      | 3V3             | VCC           |
      | VSS             | GND           |
      | PS2_CMD         | TX            |
      | PS2_DAT         | RX            |

      Setting baudrate module HC-05 / HM-10 harus sama dengan yang ada di file config [**REMOTEXY_SERIAL_SPEED**](https://github.com/AutoPlantBali/AutoPlantBali_RC?tab=readme-ov-file#configuration-file)

      **Model 1**
      ![remotexy_model1_1](/doc/image/TX/remotexy_model1_1.png)
      ![remotexy_model1_2](/doc/image/TX/remotexy_model1_2.png)

      **Model 2**
      ![remotexy_model2_1](/doc/image/TX/remotexy_model2_1.png)
      ![remotexy_model2_2](/doc/image/TX/remotexy_model2_2.png)

    * ### LCD Display TX
      LCD OLED 0.91 Inch 128x32 I2C
      ![lcd_oled_pinout](/doc/image/TX/lcd_oled_pinout.png)

      | TX PIN          | LCD OLED 0.91 Inch |
      |:----------------|:-------------------|
      | 3V3             | VCC                |
      | VSS             | GND                |
      | SCL             | SCL                |
      | SDA             | SDA                |    

* ### Profiles:
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
    
    ![web_config](doc/image/TX/web_config.png)

## Receiver AutoPlantBali RC
Marketplace: [Tokopedia](https://tokopedia.link/P3PEw5BOzPb)
* ### Receiver Wiring Diagram

  ![rx_diagram](/doc/image/RX/rx_diagram.png)
  
* ### Configuration File

| KEY                           | VALUE                             | KETERANGAN         |
|:------------------------------|:---------------------------------:|:-------------------|
| VERSION                       |                                   | Versi dari firmware rx|
| DEVELOP                       |                                   | Pembuat firmware|
| WIFI_CHANNEL                  | 1 - 11, Default: 3                | Range channel wifi dan kombinasi dengan key sebagai kode unik ke TX|
| KEY                           | 0 - 65535, Default: 0             | Key yang dikombinasi dengan channel wifi sebagai kode unik ke TX|
| WIFI_PASSWORD                 | Password wifi rx                  | Password wifi RX|
| LR_MODE                       | 1 or 0, Defualt: 0                | Set 1 untuk mode Long Range dan 0 untuk mode normal|
| LOG_ACTIVE                    | 1 or 0, Default: 0                | Set 1 untuk mengaktifkan openlog dan 0 untuk menonaktifkannya|
| SBUS_ACTIVE                   | 1 or 0, Default: 0                | Set 1 untuk masuk ke mode RX SBUS output dan 0 untuk masuk ke RC mode|
| RC_MODE                       | 1 - 7, Default: 1                 | Setting [RC Mode](https://github.com/AutoPlantBali/AutoPlantBali_RC/tree/main#mode-receiver-rc), lepas semua yang terhubung ke pin RX sebelum melakukan perubahan|
| LOG_BAUDRATE                  | max 4000000                       | Setting speed baudrate dari openlog|
| ESC_CALIBRATION               | 1 or 0, Default: 0                | ESC calibraton saat pertama kali dihidupkan (khusus untuk ESC simonk)|
| UPDATE_FIRMWARE               | 1 or 0, Default: 0                | Set 1 untuk melakukan update firmware, pastikan file firmware.bin ada di microSD card|

* ### PWM Brushed

  ![pwm_switch](/doc/image/RX/pwm_switch.png)

* ### PWM H-Bridge

  ![](/doc/image/RX/ta6586-circuit-diagram.jpg)
  
* ### Mode Receiver RC:
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

6.  **Mode 6 (RC Car / Boat)**

    | CHANNEL         | SIGNAL      | KETERANGAN         |
    |----------------:|------------:|-------------------:|
    | CHANNEL 1       | Aileron     | Servo Steering     |
    | CHANNEL 2       | Elevator    | Servo              |
    | CHANNEL 3       | Throttle    | PWM H-Bridge (IN1) |
    | CHANNEL 4       | Throttle    | PWM H-Bridge (IN2) |

7.  **Mode 7 (RC Tank)**

    | CHANNEL         | SIGNAL      | KETERANGAN               |
    |----------------:|------------:|-------------------------:|
    | CHANNEL 1       | Aileron     | Left PWM H-Bridge (IN1)  |
    | CHANNEL 2       | Aileron     | Left PWM H-Bridge (IN2)  |
    | CHANNEL 3       | Throttle    | Right PWM H-Bridge (IN1) |
    | CHANNEL 4       | Throttle    | Right PWM H-Bridge (IN2) |

* ### SBUS Output Receiver
* ### Openlog
* ### Quadcopter Drone (MultiWii)

## Battery AutoPlantBali RC
* Battery 1S with PH2.0 Plug Connector
* Weight: 18gr
* dimension: 37mm x 13mm
* Max charger 0.5A

![battery_weight](/doc/image/BATTERY/battery_weight.jpg)
![battery_capacity](/doc/image/BATTERY/battery_capacity.jpg)
