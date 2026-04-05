## FreeRTOS

```c++
void task1(void *pvParameters)
{
    while (1) {
        vTaskDelay(pdMS_TO_TICKS(1000)); // 延时1秒
    }
}

void setup()
{
    xTaskCreate(
      task1,   // 任务函数
      "Task1", // 任务名字
      4096,    // 栈大小
      NULL,    // 参数
      1,       // 优先级
      NULL     // 任务句柄
  );
}
```

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

需求库：

- IRremoteESP8266

```c++
#include <IRremoteESP8266.h>
#include <IRrecv.h>
IRrecv irrecv(15);
decode_results results;

```
