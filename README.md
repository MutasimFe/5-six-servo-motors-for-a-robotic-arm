# 5 - six servo motors for a robotic arm of the evaluation robot 

![Screenshot_3](https://user-images.githubusercontent.com/85455361/124705407-4b38b880-defe-11eb-9f68-1afa998dbb38.jpg)

# The Main Idea:

Connect 6 servo motors for evaluation robot arms and every 3 servos control 1 arm. Then set an initial position for the arms and three movements at least for the arms for interaction.

# Components:

1. Arduino 
2. Servo motors x6
3. Battery
4. Capacitors x2
5. Voltage regulator 


# Connection:

![Task 5 - six servo motors for robotic arm ( evaluation robot ) ](https://user-images.githubusercontent.com/85455361/124705388-470c9b00-defe-11eb-8635-20d412b3711d.png)

### Notes:

1. The batteries and voltage regulators are chosen because the real components are not available in Tinkercad


## Movements

Besides the initial movement I have chosen five modes for the evaluation robot which are :

1. Attention mode; which operate to attract people attentions around .
2. Welcoming mode; which operate when customer is nearby ( in evaluation range ).
3. Happy mode or what i call it " على راسي" ; which operate after the evaluation process by the customer ( if the evaluation was good ).
4. Sad mode ; which operate after the evaluation process by the customer ( if the evaluation was bad ).
5. Bye mode ; which says good bye.

###  Notes

1. The degrees are based on imagination so they can be easily adjusted based on simple math after designing the arms by the mechanical engineer. 

# Video:

### Notes

1. Each movement can be done after inter a specific letter that i set before. 
2. Some servos are in opposite direction because they are in opposite direction inside the arms.
3. In next section is about code but before that, I want to mention that I used serial communication just for presenting the modes.


# Code:

1. Defning:


2. Setup:


3. The main body (Movements)

### Note:

1. I used the delay function after the movement before it returns to its initial position, however, the delay time depends on the evaluation robot and it can easily be adjusted.


# Suggested Ideas: 

###  (1) More servo motors 

At least one more for more flexible and movements parts of the arm so we can make even more movements.
