# Temperature-Sensor
#include "DHT.h"
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27,16,2);
DHT sensor(2,DHT11);
int a =4 ,b=5,c=6,d=7,e=8,f=9,g=10;
void setup() {
  pinMode(a,OUTPUT);
  pinMode(b,OUTPUT);
  pinMode(c,OUTPUT);
  pinMode(d,OUTPUT);
  pinMode(e,OUTPUT);
  pinMode(f,OUTPUT);
  pinMode(g,OUTPUT);
  sensor.begin();
  lcd.init();
  lcd.backlight();
  lcd.clear();
}

void loop() {
  lcd.clear();
  float Temp = sensor.readTemperature();
  float Hum = sensor.readHumidity();
  lcd.setCursor(0,0);
  lcd.print("Temperature = ");
  lcd.print((int)Temp);
  lcd.print(" C");
  lcd.setCursor(0,1);
  lcd.print("Humidity = ");
  lcd.print((int)Hum);
  lcd.print(" %");
  delay(500);
  if(Temp > 32 )
  {lcd.clear();
  lcd.print("Hot");
  digitalWrite(a,LOW);digitalWrite(b,HIGH);digitalWrite(c,HIGH);
  digitalWrite(d,LOW);digitalWrite(e,HIGH);digitalWrite(f,HIGH);
  digitalWrite(g,HIGH);
  }
  else
  {
  lcd.clear();
  lcd.print("cool");
  digitalWrite(a,HIGH);digitalWrite(b,LOW);digitalWrite(c,LOW);
  digitalWrite(d,HIGH);digitalWrite(e,HIGH);digitalWrite(f,HIGH);
  digitalWrite(g,LOW);
  }
  
}
