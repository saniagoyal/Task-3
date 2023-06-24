# Task-3
#include <DS3231.h>
#include <LiquidCrystal.h>
DS3231 rtc(SDA, SCL);
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
 
void setup() {
rtc.begin();
lcd.begin(16,2);
rtc.setDOW(SUNDAY); // Set Day-of-Week
rtc.setTime(18, 50, 35); // Set the time to 12:00:00 (24hr format)
rtc.setDate(16, 12, 2018); // Day, Month, Year
}
 
void loop() {
lcd.setCursor(0,0);
lcd.print("Real Time Clock ");
 
lcd.setCursor(0,1);
lcd.print("Time: ");
lcd.print(rtc.getTimeStr());
delay(3000);
 
lcd.setCursor(0,1);
lcd.print("Date: ");
lcd.print(rtc.getDateStr());
delay(3000);
 
lcd.setCursor(0,1);
lcd.print("Day: ");
lcd.print(rtc.getDOWStr());
lcd.print(" ");
delay(3000);
 
lcd.setCursor(0,1);
lcd.print("Temp: ");
lcd.print(rtc.getTemp());
lcd.print(" C");
lcd.print(" ");
delay(3000);
}
