# safe-tracking-system
An embedded systems project focused on building a safe money tracking system.
# Safe Money Tracking System

## Overview

An embedded systems project designed to keep track of the amount of money stored in the system and display the current balance on an LCD screen.

## Features

- Displays the current balance on an LCD screen
- Allows money to be deposited
- Allows money to be withdrawn
- Updates the displayed balance in real time
- Designed with safe and reliable operation in mind

## How It Works

The system uses a microcontroller to keep track of the user's balance. Input controls allow the user to deposit or withdraw money, while an LCD provides a real-time display of the current balance.

## Technologies & Concepts

- Arduino / Microcontroller
- Embedded C/C++
- LCD display
- User input
- Variables and program logic
- Hardware/software integration

## Current Progress

🚧 **Work in Progress**

The core money tracking functionality has been implemented and tested. Additional improvements and refinements are still being developed.

## Code in Progress:
#include <LiquidCrystal.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

long potValue; // value of potentiometer being read
int state = 0; // not being used
int dollarAmount; // display dollar number 
const int buttonPin = 7; // confirm button connected to pin 7 on Arduino
const int buttonPin2 = 9;
const int buttonPin3 = 8;
int previous;
int current;
int deposit;
int withdraw;

void setup() {
  Serial.begin(9600); 
  pinMode(buttonPin, INPUT_PULLUP); // sets up our push button to be connected to pin 7
  pinMode(buttonPin2, INPUT_PULLUP);
  pinMode(buttonPin3, INPUT_PULLUP);
  lcd.begin(16, 2); // sets up an LCD display of 16 columns and 2 rows
   lcd.print("Welcome Julio!"); // welcomes the user! In this case me! :)
  previous = HIGH;
}

void loop() {

 Serial.println(digitalRead(A0));
  current = digitalRead(buttonPin);  // here we use LOW and NOT HIGH because earlier INPUT-PULLUP keep the signal into the button as a HIGH


 if(current == LOW && previous == HIGH) {
 state = state + 1;
  lcd.clear();
 }

 if(state == 1 && current == LOW && previous == HIGH){ // had to repeat current == LOW && previous == HIGH due to diplay issue
  lcd.print("Deposit or");
  lcd.setCursor(0, 1);
  lcd.print("Withdraw?");
 }

  if(digitalRead(buttonPin2) == LOW) {
  lcd.clear();
  potValue = analogRead(A0);
  dollarAmount = (potValue * 100) / 1023;
 
  lcd.setCursor(0, 0);
  lcd.print(dollarAmount);
  lcd.print("   ");
  state = state + 1;
  }
  
 previous = current;
delay(100);

## Project Media

Photos and videos demonstrating the system will be added here.

## Future Improvements

- Improve the physical interface
- Add additional security features
- Improve error handling
- Further refine the user experience
