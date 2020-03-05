#include <Wire.h>
#include <SPI.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define OLED_RESET 4
Adafruit_SSD1306 display(OLED_RESET);

#define NUMFLAKES 10
#define XPOS 0
#define YPOS 1
#define DELTAY 2
double count=0;

#define LOGO16_GLCD_HEIGHT 16
#define LOGO16_GLCD_WIDTH  16

#if (SSD1306_LCDHEIGHT != 32)
#error("Height incorrect, please fix Adafruit_SSD1306.h!");
#endif

float voltage = 0.0;
float current = 0.0;
float power = 0.0;
float Voltage = 0.0;
float Current = 0.0;

void setup() {
  Serial.begin(9600);
  display.begin(SSD1306_SWITCHCAPVCC, 0x3C);
  display.display();
  delay(2000);
  display.clearDisplay();
}

void loop() {   
  // put your main code here, to run repeatedly:
  voltage = analogRead(A1);
  current = analogRead(A0);
  Voltage = voltage * (5.0/1023.0) * 6.46;
  Current = current * (5.0/1023.0) * 0.239;
  power = voltage * current;
  String Voltage = String(count,2);
  String Current = String(count,2);
  String power = String(count,2);
  display.clearDisplay();
  robojaxText("Voltage:      ", 4,3,1,false);
  robojaxText(Voltage, 72,3,1,false);
  robojaxText("V",110,3,1,false);
  robojaxText("Current:     ", 4,13,1,false);
  robojaxText(Current, 72,13,1,false);
  robojaxText("A", 110,13,1,false);
  robojaxText("Power:       ", 4,22,1,false);
  robojaxText(power, 72,22,1,false);
  robojaxText("W",110,22,1,false);
  display.drawRect(1,1,126,31,WHITE);
  display.display();
  delay(2000);
}

void robojaxText(String text, int x, int y, int size, boolean d){

  display.setTextSize(size);
  display.setTextColor(WHITE);
  display.setCursor(x,y);
  display.println(text);
  if(d){
    display.display();
  }
  
  }
