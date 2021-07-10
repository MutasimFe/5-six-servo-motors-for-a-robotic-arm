# 5 - six servo motors for a robotic arm of the evaluation robot 

![Screenshot_3](https://user-images.githubusercontent.com/85455361/124705407-4b38b880-defe-11eb-9f68-1afa998dbb38.jpg)

# The Main Idea:

Connect 6 servo motors for evaluation robot arms each 3 servos control 1 arm. Then set an initial position for the arms and three movements at least for the arms for interaction.

# Components:

1. Arduino 
2. Servo motors MG995 x6
3. Battery
4. Capacitors x2
5. Voltage regulator Lm317; but in tinkercad we i am using 5 volt voltage regulator instead.

## MG995 Servo Motor:

![MG995-Servo-Pinout](https://user-images.githubusercontent.com/85455361/125038290-ecaa4080-e09d-11eb-9b9f-f8967cbb6d89.png)

### As shown the servomotor has 3 pins:

1. Vcc (Red) ; power pin which must connect to the voltage source.
2. Ground (Brown); ground pin.
3. Singla (Orange); which is responsible for controling the degree of the brush and it must be connected to a PWM pin. 

# Connection:

![Task 5 - six servo motors for robotic arm ( evaluation robot ) ](https://user-images.githubusercontent.com/85455361/124705388-470c9b00-defe-11eb-8635-20d412b3711d.png)

### Notes:

* The batteries and voltage regulators are chosen because the real components are not available in Tinkercad

## Movements

Besides the initial movement I have chosen five modes for the evaluation robot which are :

1. Attention mode; which operate to attract people attentions around .
2. Welcoming mode; which operate when customer is nearby ( in evaluation range ).
3. Happy mode or what i call it " على راسي" ; which operate after the evaluation process by the customer ( if the evaluation was good ).
4. Sad mode ; which operate after the evaluation process by the customer ( if the evaluation was bad ).
5. Bye mode ; which says good bye.

###  Notes

* The degrees are based on imagination so they can be easily adjusted based on simple math after designing the arms by the mechanical engineer. 

# Video:

https://user-images.githubusercontent.com/85455361/125160841-e0021700-e187-11eb-8e99-9c368238ec9a.mp4

### Notes

* Each movement can be done after inter a specific letter that i set before. 
* Some servos are in opposite direction because they are in opposite direction inside the arms.
* In next section is about code but before that, I want to mention that I used serial communication just for presenting the modes.

# Code:

* Library:

``` c++
  #include<Servo.h>
  ```
  
* Defning:

``` c++
  Servo servo1; //first hard
  Servo servo2; //first hand
  Servo servo3; //first hand

  Servo servo4; //second hand
  Servo servo5; //second hand
  Servo servo6; //second hand

  char Byte; //for chosing the mode.

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
```

* Setup:

``` c++

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
```


* The main body (Movements)

``` c++
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

``` 
* Modes

``` c++

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
```

### Note:

* I used the delay function after the movement before it returns to its initial position, however, the delay time depends on the evaluation robot and it can easily be adjusted.

# Suggested Ideas: 

###  (1) More servo motors 

At least one more for more flexible and movements parts of the arm so we can make even more movements.
