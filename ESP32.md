## Arduino
### I/O
[`pinMode(pin, mode)`](https://docs.arduino.cc/language-reference/en/functions/digital-io/pinMode/)
[`digitalWrite(pin, val)`](https://docs.arduino.cc/language-reference/en/functions/digital-io/digitalwrite/)
### Serial
[`Serial.begin(baud)`](https://docs.arduino.cc/language-reference/en/functions/communication/serial/begin/)
`Serial.printf(const char *format, ...)`

## FreeRTOS

| 作用     | 代码                                                                                                                              |
| -------- | --------------------------------------------------------------------------------------------------------------------------------- |
| 声明函数 | `void task1(void *pvParameters)`                                                                                                  |
| 创建任务 | [`xTaskCreate()`](https://www.freertos.org/zh-cn-cmn-s/Documentation/02-Kernel/04-API-references/01-Task-creation/01-xTaskCreate) |
| 延时     | [`vTaskDelay(pdMS_TO_TICKS(MS))`](https://www.freertos.org/zh-cn-cmn-s/Documentation/02-Kernel/04-API-references/02-Task-control/01-vTaskDelay)    |

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
#include <IRrecv.h>

IRrecv irrecv(15);
decode_results results;

void setup() {
  Serial.begin(115200);
  irrecv.enableIRIn();
}

void loop() {
  if (irrecv.decode(&results))
  {
    irrecv.resume();
    if (results.decode_type == -1)
        continue;
    Serial.printf("协议：%d|地址：%X|命令：%X|重复：%d\n", results.decode_type, results.address, results.value, results.repeat);
  }
  delay(100)
}
```
####
```c++


```
### 发送

```c++
#include <ir_Coolix.h> //需要的品牌空调库

IRCoolixAC ac(pin);

ac.begin();
ac.on();
ac.send();
```
```c++
#include <IRsend.h>

IRsend irsend(pin);

irsend.begin();
irsend.sendNEC();
irsend.sendRaw();
```