## ST7735S 显示屏

需求库：

- TFT_eSPI

## DS18B20 温度传感器

需求库：

- OneWire
- DallasTemperature

```c++
#include <OneWire.h>
#include <DallasTemperature.h>

const int oneWireBus = 4;

OneWire oneWire(oneWireBus);
DallasTemperature sensors(&oneWire);
void setup() {
    Serial.begin(115200);
    sensors.begin();
}
void loop() {
    sensors.requestTemperatures();
    float temperatureC = sensors.getTempCByIndex(0);
    float temperatureF = sensors.getTempFByIndex(0);
    Serial.print("Temperature: ");
    Serial.print(temperatureC);
    Serial.print("°C / ");
    Serial.print(temperatureF);
    Serial.println("°F");
    delay(5000);
}
```

## 红外收发模块

库：

- IRremoteESP8266
