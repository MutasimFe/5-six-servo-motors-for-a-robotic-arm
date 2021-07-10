// 6 servo motors of a robotic arm

#include<Servo.h>

Servo servo1; //first hard
Servo servo2; //first hand
Servo servo3; //first hand

Servo servo4; //second hand
Servo servo5; //second hand
Servo servo6; //second hand

char Byte;

int servoPin1 = 3;
int servoPin2 = 5;
int servoPin3 = 6;

int servoPin4 = 9;
int servoPin5 = 10;
int servoPin6 = 11;

int iniPos1 = 0;
int iniPos2 = 0;
int iniPos3 = 20;

int iniPos4 = 180; // 180 because it is in opposite location
int iniPos5 = 180;
int iniPos6 = 160;


void setup()

{

  Serial.begin(9600);

  servo1.attach(servoPin1);
  servo2.attach(servoPin2);
  servo3.attach(servoPin3);

  servo4.attach(servoPin4);
  servo5.attach(servoPin5);
  servo6.attach(servoPin6);

  servo1.write(iniPos1);
  servo2.write(iniPos2);
  servo3.write(iniPos3);

  servo4.write(iniPos4);
  servo5.write(iniPos5);
  servo6.write(iniPos6);

}

void loop()
{

  servo1.write(0); //initial pos (all arms are down)
  servo2.write(0);
  servo3.write(20);

  servo4.write(180);
  servo5.write(180);
  servo6.write(160);
  delay(3000);


  if (Serial.available() > 0) // if there is a signal coming from outside it will join the loop
  {

    Byte = Serial.read(); // for reading and store from outside

    if (Byte == 'A') // Attention mode ( waving )
    {
      servo1.write(120);
      servo2.write(40);
      servo3.write(0);

      servo4.write(40);
      servo5.write(140);
      servo6.write(180);
      delay(2000);

      servo3.write(40); //Two hands are waving
      servo6.write(140);
      delay(2000);

      servo3.write(0);
      servo6.write(180);
      delay(2000);

      servo3.write(40);
      servo6.write(140);
      delay(2000);

      servo3.write(0);
      servo6.write(180);
      delay(2000);
    }

    else if (Byte == 'W') // Welcome mode
    {
      servo1.write(70); // two arms are forward
      servo2.write(20);
      servo3.write(30);

      servo4.write(110);
      servo5.write(160);
      servo6.write(150);
      delay(5000);

    }

    else if (Byte == 'H') // Happy mode
    {
      servo1.write(160); //Toucing his head "على راسي"
      servo2.write(20);
      servo3.write(90);

      servo4.write(20);
      servo5.write(160);
      servo6.write(90);
      delay(3000);
      
      servo3.write(70);
      servo6.write(110);
      delay(2000);
      
      servo3.write(90);
      servo6.write(90);
      delay(2000);
      
      servo3.write(70);
      servo6.write(110);
      delay(2000);
      
      servo3.write(90);
      servo6.write(90);
      delay(2000);

    }

    else if (Byte == 'S') // Sad mode
    {
      servo1.write(0); //Free down arm
      servo2.write(0);
      servo3.write(0);

      servo4.write(180);
      servo5.write(180);
      servo6.write(180);
      delay(5000);


    }

    else if (Byte == 'G') // Good bye mode
    {
      servo1.write(120);
      servo2.write(40);
      servo3.write(0);

      servo4.write(180);
      servo5.write(180);
      servo6.write(160);
      delay(3000);

      servo3.write(40); //One hand  is waving
      delay(2000);

      servo3.write(0);
      delay(2000);

      servo3.write(40);
      delay(2000);

      servo3.write(0);
      delay(2000);


    }
  }
}
