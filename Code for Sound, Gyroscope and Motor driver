//Sound sensor
const int soundSensorPin = 5; // set the analog input pin for the sound sensor
//Motor driver
int in1 = 8; // set the digital output pin for input 1
int in2 = 9; // set the digital output pin for input 2
int enA = 10; // set the digital output pin for PWM signal

//Gyroscope
#include "Arduino.h"
#include "U8g2lib.h"
#include "Wire.h"
const int xpin = A3; // x-axis of the accelerometer
const int ypin = A1; // y-axis
const int zpin = A2; // z-axis
U8G2_SSD1306_128X64_NONAME_F_HW_I2C u8g2(U8G2_R0, /* reset=*/ U8X8_PIN_NONE);
 

void setup() {
  Serial.begin(9600); // for debugging purposes
  //Motor driver
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(enA, OUTPUT);
  
   //Gyroscope
  Wire.begin();
  u8g2.begin();

}


void loop() {
  //Sound sensor
  int soundValue = analogRead(soundSensorPin); // read the analog input from the sound sensor
  Serial.println(soundValue); // for debugging purposes
  if(soundValue<1175)
  {
Serial.println("Baby is happy and in peace");
  }
  else{
Serial.println("Baby is sad.");
   /* digitalWrite(in1, HIGH); // set input 1 high
    digitalWrite(in2, LOW); // set input 2 low
    analogWrite(enA, 255); // set PWM signal to maximum (255)
    delay(5000); // run the motor forward for 5 seconds

    digitalWrite(in1, LOW); // set input 1 low
    digitalWrite(in2, HIGH); // set input 2 high
    analogWrite(enA, 200); // set PWM signal to a lower value (200)
    delay(5000); // run the motor backward for 5 seconds*/

    unsigned long startMillis = millis(); // get the current time
    while(millis() - startMillis < 5000) { // run the loop for 30 seconds
      digitalWrite(in1, HIGH); // set input 1 high
      digitalWrite(in2, LOW); // set input 2 low
      analogWrite(enA, 255); // set PWM signal to maximum (255)
    delay(5000); // run the motor forward for 1 second

      digitalWrite(in1, LOW); // set input 1 low
      digitalWrite(in2, HIGH); // set input 2 high
      analogWrite(enA, 200); // set PWM signal to a lower value (200)
      delay(5000); // run the motor backward for 1 second
    }      
  } // add a small delay to avoid flickering
    delay(1000);

//Gyroscope
int x = analogRead(xpin); //read from xpin
delay(1); //
int y = analogRead(ypin); //read from ypin
delay(1); 
int z = analogRead(zpin); //read from zpin
 
float zero_G = 512.0; //ADC is 0~1023 the zero g output equal to Vs/2
float scale = 102.3; //ADXL335330 Sensitivity is 330mv/g
//330 * 1024/3.3/1000
 //print x value on serial monitor
float x1=(((float)x - 331.5)/65*9.8);
Serial.print(" x:");
Serial.print(x1);
 //print y value on serial monitor
float y1=(((float)y - 329.5)/68.5*9.8);
Serial.print(" y:");
Serial.print(y1);
//print z value on serial monitor
float z1=(((float)z - 340)/68*9.8);
Serial.print(" z:");
Serial.println(z1);

if(613.00>x1|| x1>800.00){
  Serial.println("Baby needs to  be checked upon");
}
 
delay(5000); 
  
  u8g2.firstPage();
  do {
   u8g2.setFont(u8g2_font_ncenB18_tr);
    u8g2.drawStr(2,20,"x :");
    u8g2.setCursor(40, 20);
            u8g2.print(x1);
    u8g2.drawStr(2,40,"y :");
        u8g2.setCursor(40, 40);
            u8g2.print(y1);
    u8g2.drawStr(2,60,"z :");
       u8g2.setCursor(40, 60);
            u8g2.print(z1);
    
  } while ( u8g2.nextPage() );
}

