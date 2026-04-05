## FreeRTOS

```c++
#include <Arduino.h>

void task1(void *pvParameters)
{
  while (1)
  {
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
#include <Arduino.h>
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
  Serial.printf("Temperature：%f°C / %f°F\n", temperatureC, temperatureF);
  delay(1000);
}
```

## 红外收发模块

需求库：

- IRremoteESP8266

### 接收

```c++
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRrecv.h>
#include <IRutils.h>

IRrecv irrecv(15);
decode_results results;

void setup() {
  Serial.begin(115200);
  sensors.begin();
}

void loop() {
  if (irrecv.decode(&results))
  {
    Serial.printf("协议：%d", results.decode_type);
    Serial.print("|地址：");
    Serial.print(results.address);
    Serial.print("|命令：");
    serialPrintUint64(results.value, HEX);
    Serial.println("");
    irrecv.resume();
  }
  delay(100)
}
```

### 发送

```c++
#include <IRsend.h>
#include <ir_Coolix.h> //需要的品牌空调库

IRsend irsend(4);
IRCoolixAC ac(4);

ac.on();
ac.send();
```
