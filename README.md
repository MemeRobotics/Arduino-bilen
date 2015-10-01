# Arduino-bilen
Första projektet: Linjeföljaren
Kod:

#include <Adafruit_MotorShield.h>
#include <lenlib.h> 
#include <Servo.h> 
#include <Wire.h> 

int R0Val = 0;
int R1Val = 0;
int R2Val = 0;

mySensors Sensors; // create Sensors object
myMotors Motors;  // create Motors object

void setup() 
{ 
  Motors.beginMotors();   // start motors
  Sensors.beginSensors(); // start sensors
}

void loop() 
{
  
  R0Val  = Sensors.readReflect0(); // Read digital value of reflect sensor 0
  R1Val  = Sensors.readReflect1(); // Read digital value of reflect sensor 1
  R2Val  = Sensors.readReflect2(); // Read digital value of reflect sensor 2

  if(R0Val == 1)
  {
      Motors.runMotor(1, FORWARD, 0); // Run motor 1 & 2 forward at 0 velocity(Stop)
      Motors.runMotor(2, FORWARD, 150);
 }
  else
  {
      Motors.runMotor(1, FORWARD, 0); // Run motor 1 & 2 forward at 150 velocity
      Motors.runMotor(2, FORWARD, 0);
 }
  
  if(R1Val == 1)
  {
      Motors.runMotor(1, FORWARD, 0); // Run motor 1 & 2 forward at 0 velocity(Stop)
      Motors.runMotor(2, FORWARD, 150);
 }
  else
  {
      Motors.runMotor(1, FORWARD, 0); // Run motor 1 & 2 forward at 150 velocity
      Motors.runMotor(2, FORWARD, 0);
      
  }
  if(R2Val == 1)
  {
     Motors.runMotor(1, FORWARD, 150); // Run motor 1 & 2 forward at 0 velocity(Stop)
      Motors.runMotor(2, FORWARD, 0);
     }
 else
  {
      Motors.runMotor(1, FORWARD, 0); // Run motor 1 & 2 forward at 150 velocity
      Motors.runMotor(2, FORWARD, 0);
  }
}
