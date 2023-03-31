# AR2040RSH Arduinoサンプルソフト

## 1. AD2040RSH_OLED
AR2040RSHにADRSZLD(OLED表示機）を搭載し表示します。
前提としてAdafruit_SSD1306とその前提ライブラリのインストールが必要です。  
ADRSZLDのSPIは、Raspberry Pi Picoの以下のGPIOにアサインされているので、Adafruitのサンプルソフトの以下を変更しています。
```
#define OLED_MOSI   11
#define OLED_CLK    10
#define OLED_CS     8
#define OLED_DC     0
#define OLED_RESET  1

Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, OLED_MOSI, OLED_CLK, OLED_DC, OLED_RESET, OLED_CS);
```

## 2. ADRSZBM(BME280温湿度・気圧センサ）
AR2040RSHにADRSZBM(BME280温湿度・気圧センサ）を搭載し、温度、湿度、気圧等を表示します。
前提としてAdafruit_BME280とその前提ライブラリのインストールが必要です。  
ADRSZBMのI2Cは、Raspberry Pi PicoのI2C1のGPIO2/GPIO3にアサインされているので、Adafruitのサンプルソフトの以下を変更しています。
```
    Wire1.setSDA(2);
    Wire1.setSCL(3);
    status = bme.begin(0x76, &Wire1);  
```