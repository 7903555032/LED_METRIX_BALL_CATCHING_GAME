# Catch the Falling Dot Game

## 1. Project Overview

This project is a simple interactive game built using an Arduino Uno, an 8×8 1088AS LED matrix, two SN74HC595N shift registers, and two push buttons.

The player controls a two-LED paddle at the bottom of the matrix and tries to catch a falling LED by moving left or right.

## 2. Components Required

| Component | Quantity |
|---|---:|
| Arduino Uno | 1 |
| 1088AS 8×8 LED matrix | 1 |
| SN74HC595N shift register IC | 2 |
| Push buttons | 2 |
| 1 kΩ resistors for SEG lines | 8 |
| 2.2 kΩ resistors for DIG lines | 8 |
| Breadboard and jumper wires | As required |
| USB cable | 1 |

## 3. Circuit Connections

### Arduino to shift registers

| Arduino pin | Connection |
|---|---|
| D2 | IC1 pin 14 (SER) |
| D3 | Both ICs pin 12 (RCLK) |
| D4 | Both ICs pin 11 (SRCLK) |
| 5V | Both ICs pin 16 (VCC) |
| GND | Both ICs pin 8 (GND) |
| 5V | Both ICs pin 10 (SRCLR) |
| GND | Both ICs pin 13 (OE) |
| IC1 pin 9 (QH′) | IC2 pin 14 (SER) |

### LED matrix connections

- IC2 outputs connect to the eight SEG lines through individual 1 kΩ resistors.
- IC1 outputs connect to the eight DIG lines through individual 2.2 kΩ resistors.

Use the matrix pinout diagram for the exact SEG and DIG pin numbers.

### Push buttons

| Button | Arduino connection | Other terminal |
|---|---|---|
| Left | D5 | GND |
| Right | D6 | GND |

The Arduino code uses `INPUT_PULLUP`, so external button resistors are not required.

**Important:** The resistor values and direct shift-register drive arrangement should be checked against the SN74HC595N current limits before prolonged operation. Series resistors alone do not guarantee safe operation under every display pattern.

## 4. Game Rules

1. A single LED falls from the top of the matrix.
2. The two-LED paddle is displayed at the bottom.
3. Press the left button to move the paddle left.
4. Press the right button to move the paddle right.
5. Catch the falling LED to increase the score.
6. Each successful catch increases the falling speed.
7. Three missed dots end the game.
8. Press either button to restart.

## 5. Software Requirements

- Arduino IDE
- Arduino AVR board support
- No external libraries required

## 6. How to Upload

1. Connect the Arduino Uno to your computer using USB.
2. Open `Catch_the_Falling_Dot_Game.txt` in a text editor.
3. Copy the complete code into a new Arduino IDE sketch.
4. Select **Tools → Board → Arduino Uno**.
5. Select the correct port under **Tools → Port**.
6. Click **Verify** to compile the program.
7. Click **Upload** to transfer the code to the Arduino.
8. Test the left and right buttons.

## 7. Troubleshooting

| Problem | What to check |
|---|---|
| Matrix remains blank | Power, ground, OE, SRCLR, and shift-register wiring |
| Paddle moves in the wrong direction | Column mapping in the code |
| Buttons do not respond | D5/D6 wiring and GND connections |
| Some LEDs do not glow | Matrix pinout, SEG resistors, and DIG connections |
| Display flickers | Row-scanning timing and current limits |
| Arduino resets unexpectedly | Power supply and LED current |

## 8. Possible Improvements

- Display the score as a number.
- Add a start screen.
- Add sound using a buzzer.
- Add multiple falling dots.
- Add different difficulty levels.
- Add a high-score feature.

## 9. Project Learning Outcomes

This project demonstrates:

- Digital output control using shift registers.
- Multiplexed LED matrix scanning.
- Push-button input handling.
- Basic game logic and collision detection.
- Timing using `millis()`.
- Random number generation and difficulty adjustment.

## 10. Author

**Project:** Arduino 8×8 LED Matrix Catch Game  
**Platform:** Arduino Uno  
**Display:** 1088AS 8×8 LED matrix  
**Control:** Two push buttons
