# OOP Battleship: Single-Player Game Engine and GUI (Part C)

## 💡 Overview
This project represents the third stage of the software engineering process. The goal is to design and implement a complex, single-player version of the classic Battleship game using a clean **Java Swing GUI** and a **strong object-oriented model**. The core challenge involves separating the intricate game logic (ship placement, hit/miss tracking) from the visual presentation.

## 🎯 Design and Implementation Goals
This lab demonstrates proficiency in:
1.  **Software Engineering Design:** Defining classes and responsibilities using the CRC card method.
2.  **Complex State Management:** Creating classes (`Board`, `Ship`, `Cell`) to manage the game's state effectively.
3.  **Advanced Logic Implementation:** Solving the non-trivial problem of randomly placing ships on the 10x10 grid without overlap.
4.  **Rich GUI Feedback:** Implementing complex counters and dialog prompts for game events (Win, Loss, Ship Sunk).

## 🛠️ Design Component Summary

The application is built on the following core domain classes:

| Class Name | Primary Responsibility | Key Logic Focus |
| :--- | :--- | :--- |
| **BattleshipGame** | Overall flow, event handling (button clicks), and managing game state transitions (e.g., win/loss checks). |
| **Board** | Represents the 10x10 grid; manages ship placement and cell state (HIT, MISS, BLANK). |
| **Ship** | Stores its length, coordinates, and tracks the number of hits sustained (determines if sunk). |
| **Cell** | Stores its coordinates and current state (essential for the visual grid). |

## ⚙️ Game Logic and Rules Implementation

### 1. **Initial Setup (Placement)**
* Five ships of varying lengths **{5, 4, 3, 3, 2}** are randomly placed on the 10x10 board.
* Ship placement logic ensures no ships overlap, checking for valid vertical or horizontal segments.

### 2. **Game Logic & Counters**
The game tracks progress using four crucial counters:
* **MISS Counter [0-5]:** Tracks consecutive misses. Reaching 5 resets this counter and increments the STRIKE counter.
* **STRIKE Counter [0-3]:** Tracks accumulated strikes (5 consecutive misses). Reaching 3 results in **Game Loss**.
* **TOTAL HIT Counter [0-17]:** Tracks total hits across all ships. Reaching 17 results in **Game Win**.
* **TOTAL MISS Counter [0-83]:** Tracks overall misses.

### 3. **GUI and Event Handling**
* The main interface is a **10x10 grid of JButtons**.
* Each button click triggers the `BattleshipGame` logic to check for a Hit or Miss and updates the cell display (X, M, or Wave image/character).
* **Dialogs** inform the user when a specific ship is sunk or when the game has ended (Win/Loss).
* The **"Play Again"** and **"Quit"** buttons use confirmation dialogs to ensure intentional action.

## 🖼️ Visual Feedback (Cell States)

| State | Visual Representation | Event |
| :--- | :--- | :--- |
| **BLANK** | Light Blue Wave | Initial state or unclicked area. |
| **MISS** | Yellow 'M' (Splash) | Player clicks an empty cell. |
| **HIT** | Red 'X' (Explosion) | Player clicks a cell containing a ship. |
