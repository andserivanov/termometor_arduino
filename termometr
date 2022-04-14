#include <RDC1_LD.h>
// библиотека для работы с протоколом 1-Wire
#include <OneWire.h>
// библиотека для работы с датчиком DS18B20
#include <DallasTemperature.h>
 
// сигнальный провод датчика
#define ONE_WIRE_BUS 6
// создаём объект для работы с библиотекой OneWire
OneWire oneWire(ONE_WIRE_BUS);
 
// создадим объект для работы с библиотекой DallasTemperature
DallasTemperature sensor(&oneWire);
//const int dt = 6;
const int grnd = 5;
int tempc = 0;
RDC1_LD Display(3, 2, 4, 2);
//  latch, data, clk,  разряды

void setup()
{
//  pinMode(dt, OUTPUT); //задаем выходы ардуины для даттчика температуры
   pinMode(grnd, OUTPUT);
   digitalWrite(grnd, LOW);
  //установка яркости на 100%
  Display.SetBrightness(30);
  //дисплей с общим катодом
  Display.SetType(COMMON_ANODE);
  Serial.begin(9600);
    // начинаем работу с датчиком
  sensor.begin();
  // устанавливаем разрешение датчика от 9 до 12 бит
  sensor.setResolution(12);
}

void loop()
{
  float temperature;
  // отправляем запрос на измерение температуры
  sensor.requestTemperatures();
  // считываем данные из регистра датчика
  temperature = sensor.getTempCByIndex(0);
  // выводим температуру в Serial-порт
  Serial.print("Temp C: ");
  Serial.println(temperature);
  Display.print(temperature);
  delay(1000); 
}
