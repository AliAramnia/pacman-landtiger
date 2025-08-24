# Pac-Man on LandTiger Board

This project brings the classic **Pac-Man game** to the **LandTiger development board**.  
The main objective is to reproduce the familiar arcade gameplay while making use of the hardware peripherals available on the board.  
It shows how game logic and embedded systems can be combined in a practical and fun way.

The entire project was developed and tested in **Keil µVision IDE** with the **ARM toolchain**, and runs directly on the LandTiger hardware (the software simulator alone is not enough).

---

## Features and Peripherals Used

- **LCD Screen**  
  The game maze, Pac-Man, ghosts, and scoring information are drawn on the integrated LCD display.  

- **Joystick / Buttons**  
  Player input is handled through the built-in joystick and push buttons, which control Pac-Man’s movement.  

- **AI Ghost (Blinky)**  
  A red ghost with simple AI behavior tries to catch Pac-Man.  
  - *Chase Mode*: moves toward Pac-Man using pathfinding.  
  - *Frightened Mode*: triggered by a Power Pill; the ghost flees, turns blue, and can be eaten for extra points.  

- **Speaker Output**  
  Background music and game sound effects are produced using the speaker.  

- **Timers**  
  Hardware timers control game timing, ghost respawn intervals, and frightened-mode duration.  

- **CAN Bus**  
  Configured in loopback mode with CAN1 and CAN2.  
  Sends a 32-bit value containing:  
  - Remaining Time (8 bits)  
  - Remaining Lives (8 bits)  
  - Score (16 bits)  
  Used to demonstrate real-time data transfer across CAN controllers.  

- **Interrupts**  
  Handle player input, timing events, and hardware coordination to ensure smooth gameplay.  

---

## CAN Bus Communication

The **Controller Area Network (CAN)** is used to broadcast the game status.  
In loopback mode, CAN1 transmits messages and CAN2 receives them, imitating two separate boards communicating.  

**Message format:**
- 8 bits → Remaining Time  
- 8 bits → Remaining Lives  
- 16 bits → Score  

All fields are packed into one **32-bit unsigned integer** for efficient communication.  

**Purpose in the game:**
- Displays how game data can be shared in real time.  
- Demonstrates standard communication protocols in an embedded project.  
- Links classic gameplay with practical hardware usage.  

---

## Requirements

- **Board:** LandTiger Development Kit  
- **Peripherals:** LCD, joystick, push buttons, speaker, timers, CAN controllers  
- **Software:** Keil µVision IDE with ARM Compiler, board drivers  

---

## Running the Project

1. Open the project in **Keil µVision IDE**.  
2. Build and compile the code.  
3. Flash the binary to the **LandTiger board**.  
4. Use the joystick to play Pac-Man.  
5. Game visuals appear on the LCD, audio plays through the speaker, and CAN messages are exchanged in loopback mode.  

---

This project demonstrates how a simple video game can be adapted to an embedded hardware platform.  
By combining **graphics, input handling, audio, timing, and communication protocols**, it shows the versatility of the **LandTiger board** in real-time applications.
