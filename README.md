# temperature-and-humibity-sensor-

Introduction
In this project, we are going to interface a DHT11 temperature and humidity sensor, and display the data on a 16x2 LCD. If you haven't read $ Project 9 $ for the Arduino Uno Rev3, please read that first because this covers how to interface a 16x2 character LCD in 4-bit mode. We will then swap out the 16x2 LCD for a 20x4 LCD to display the humidity and the temperature in Celsius, Fahrenheit, and Kelvin. The DHT11 sensor can be used for a weather station, weather balloon, drone, or greenhouse

16x2 Character LCD
In our previous project, we showed you how to interface a 16x2 LCD to the Uno. You should have pins 4, 6, and 11 - 14 of the LCD connected to Uno pins 2, 3, and 4 - 7, respectively. You can either connect the LCD using a solderless breadboard or the Modulus Canister. An image is shown below with it connected to Modulus. 

Code
//Interface the DHT11 Temp & Humidity sensor and display humidity and  temperature
//in Celsius on a 16x2 character LCD

#include <dht.h>
#include  <LiquidCrystal.h>

dht DHT;
const int RS = 2, EN = 3, D4 = 4, D5 = 5, D6  = 6, D7 = 7;
LiquidCrystal lcd(RS,EN,D4,D5,D6,D7);   //set Uno pins that are  connected to LCD, 4-bit mode

void setup() {
  lcd.begin(16,2);    //set  16 columns and 2 rows of 16x2 LCD

}

void loop() {
  int readDHT  = DHT.read11(8);    //grab 40-bit data packet from DHT sensor
  lcd.setCursor(0,0);  
  lcd.print("Temp: ");
  lcd.print(DHT.temperature);
  //lcd.print((char)223);         //used to display degree symbol on display
  //lcd.write(0xdf);              //another  way to display degree symbol
  lcd.print("C");
  lcd.setCursor(0,1);
  lcd.print("Humidity: ");
  lcd.print(DHT.humidity);
  lcd.print("%");
  delay(3000);

}



Circuit diagram    
![image](https://github.com/user-attachments/assets/b9dd57d6-794a-4ce4-9dcb-2254eea2eeeb)

 
Output 
 ![image](https://github.com/user-attachments/assets/f59bef87-1f81-4d50-902a-a98f55b7108a)

