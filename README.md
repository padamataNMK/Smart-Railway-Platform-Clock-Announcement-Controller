# 🚆 Smart Railway Platform Clock Announcement Controller

A real-time railway platform information and train monitoring system developed using the LPC2148 ARM7 microcontroller.

Real-Time Train Information • Smart Alerts • Admin Control

---

## 📌 Project Overview

The Smart Railway Platform Clock Announcement Controller is an embedded system designed to monitor railway schedules and provide real-time platform information to passengers.

The system uses an RTC (Real-Time Clock) to maintain the current date and time and compares the current time with the updated train timings. When a train is approaching, its information is displayed on the 16×2 LCD along with appropriate LED and buzzer indications.

The system also provides an Admin Mode through an external interrupt. An authorized user can access the administration menu using PIN authentication and modify RTC settings or selected train information through the 4×4 keypad. Input validation and platform collision checking are performed before changes are saved.

---

## 🎯 Objectives

- 🕒 Display the current date and time using the RTC.
- 🚆 Maintain information for multiple trains.
- 📺 Display train number, name, destination, timing and platform information.
- ⏱️ Detect trains approaching within the configured time window.
- 🚦 Indicate train status using Green, Yellow and Red LEDs.
- 🔊 Provide an audible alert using a buzzer.
- 🔄 Scroll long train names on the LCD.
- 🔐 Provide protected Admin Mode using PIN authentication.
- ✏️ Allow authorized modification of RTC and train information.
- 🛤️ Check platform timing conflicts before saving changes.
- ✅ Validate entered values before updating the train database.

---

## 🧩 System Block Diagram

<img width="1536" height="1024" alt="IMG-20260917-WA0003" src="https://github.com/user-attachments/assets/09b45e78-c3e7-4f12-89ec-8aeeeff8f138" />



---

## 🧠 Project Mind Map


<img width="1536" height="1024" alt="WhatsApp Image 2026-09-15 at 10 06 09 PM (3)" src="https://github.com/user-attachments/assets/8c4312cc-145d-47bd-b232-b255a11463f4" />



---

## ⚙️ System Working

The system works mainly in two modes: Normal Mode and Admin Mode.

### 🟢 Normal Mode

- Initializes the required hardware peripherals.
- Reads the current date and time from the RTC.
- Compares the current time with updated train schedules.
- Detects trains that are within 5 minutes of arrival and have not yet departed.
- Displays approaching train information on the LCD.
- Shows train summaries when no train is approaching.
- Provides LED and buzzer indications according to the train condition.
- Handles multiple active trains one after another.
- Automatically changes the display after a train's departure time has elapsed.

### 🔐 Admin Mode

- Activated through the Admin switch connected to the external interrupt.
- The interrupt service routine sets the Admin Mode flag.
- The user enters the PIN for authorization.
- The administrator can select RTC settings or train-data modification.
- Entered values are checked before saving.
- Platform timing conflicts are checked before accepting changes.
- Valid delay values are used to recalculate updated arrival and departure timings.

---

## 🔐 Admin Mode & Validation

The Admin Mode provides controlled access to the railway schedule and RTC configuration.

### Admin Operations

- 🔑 PIN-based authentication
- 🕒 RTC date and time modification
- 🚆 Train selection
- ⏱️ Delay modification
- 🛤️ Platform modification
- 🕐 Arrival time modification
- 🕐 Departure time modification

### Validation & Safety

Before updating the train information, the system checks:

- Platform number range
- Delay value
- Arrival time format
- Departure time format
- Platform availability during the selected schedule
- Timing overlap with other trains

Only valid information is accepted and saved. When a delay is applied, the updated arrival and departure times are recalculated automatically.

---

## 🔧 Hardware Requirements

| Component | Purpose |
|---|---|
| LPC2148 | Main ARM7 microcontroller |
| 16×2 LCD | Displays time, train and menu information |
| 4×4 Matrix Keypad | User input and Admin Mode operations |
| RTC | Maintains real-time date and time |
| Green LED | On-time indication |
| Yellow LED | Approaching indication |
| Red LED | Delayed indication |
| Buzzer | Audio alert |
| Admin Switch | External interrupt for Admin Mode |
| USB-UART Converter / DB-9 Cable | Serial communication / programming support |

---

## 💻 Software & Tools

| Tool / Technology | Purpose |
|---|---|
| Embedded C | Application programming |
| Keil µVision | Embedded C development and compilation |
| Flash Magic | LPC2148 programming / flashing |
| LPC2148 | Target microcontroller |
| ARM7TDMI-S | Processor architecture |

---

## ✨ Key Features

- 🕒 **Real-Time Monitoring** — Maintains the current date and time using RTC.
- 🚆 **Train Database** — Stores information for multiple trains.
- ⏱️ **Approaching Train Detection** — Detects trains approaching within 5 minutes.
- 📺 **LCD Information Display** — Shows train details, timing and platform information.
- 🔄 **Scrolling Display** — Scrolls long train names on the LCD.
- 🚦 **LED Indication** — Indicates on-time, approaching and delayed conditions.
- 🔊 **Buzzer Alert** — Gives an audible indication when a train is approaching.
- 🔐 **PIN Authentication** — Restricts access to Admin Mode.
- ⚡ **External Interrupt** — Uses EINT0 to activate Admin Mode.
- 🛤️ **Platform Collision Detection** — Checks overlapping train schedules on the same platform.
- ✅ **Input Validation** — Checks RTC and train-data inputs before saving.
- 🔁 **Automatic Timing Update** — Recalculates updated timings after a delay is entered.

---

## 🧠 Key Implementation Concepts

The project combines several embedded-system concepts to implement real-time railway monitoring.

- 🕒 **RTC-Based Time Comparison** — Compares the current RTC time with train timings.
- 🔢 **Time-to-Minutes Conversion** — Converts hours and minutes into minutes for easier calculations.
- 🚆 **Multiple Train Handling** — Maintains and processes multiple train records.
- 📺 **LCD Scrolling** — Displays long train names using a scrolling mechanism.
- ⚡ **External Interrupt Handling** — Uses EINT0 to enter Admin Mode.
- 🔐 **Menu State Handling** — Controls the different stages of the Admin and RTC menus.
- ✅ **Input Validation** — Checks entered values before accepting changes.
- 🛤️ **Platform Collision Checking** — Detects schedule overlap for trains assigned to the same platform.
- 🔁 **Automatic Timing Recalculation** — Updates arrival and departure timings according to delay.
- 🧩 **Modular Design** — Separates application logic, drivers and supporting modules.

---

## 📂 Project Structure

```text
Smart-Railway-Platform-Clock-Announcement-Controller/
│
├── types.h
│
├── train_main.c
│
├── railway.c
├── railway.h
│
├── train_dprint.c
├── train_dprint.h
│
├── admin.c
├── admin.h
│
├── RTC.c
├── RTC.h
│
├── lcd.c
├── lcd.h
│
├── keypad.c
├── keypad.h
│
├── indicator.c
├── indicator.h
│
├── interrupt.c
├── interrupt.h
│
├── delay.c
├── delay.h
│
├── images/
│   ├── block-diagram.png
│   ├── project-mind-map.png
│   └── system-flow.png
│
└── README.md
```

---

## 🧩 Module Description

| Module | Responsibility |
|---|---|
| `train_main.c` | Main application flow and system control |
| `railway.c` | Train database and train information |
| `train_dprint.c` | Train summaries, approaching-train display and scrolling |
| `admin.c` | Admin menu, data editing, validation and collision checking |
| `RTC.c` | RTC initialization, date/time handling and RTC editing |
| `lcd.c` | 16×2 LCD driver and display operations |
| `keypad.c` | 4×4 keypad scanning and key detection |
| `indicator.c` | LED and buzzer control |
| `interrupt.c` | External interrupt configuration and ISR |
| `delay.c` | Delay generation |
| `*.h` | Function declarations, structures and macros |

---

## 🔄 System Workflow

The overall system continuously monitors the RTC and train schedule information.


<img width="1024" height="1536" alt="ChatGPT Image Sep 15, 2026, 10_17_57 PM" src="https://github.com/user-attachments/assets/994b1413-86df-47a6-ad30-3ff73eef99d2" />


---

## 🖥️ Simulation & Output

The system is designed around an LPC2148-based embedded controller with a 16×2 LCD, 4×4 keypad, RTC, status LEDs, buzzer and an external Admin switch.

### 🔬 Main Output Behaviour

- Current date and time are displayed through the LCD.
- Train information is displayed when the corresponding train becomes active.
- Long train names are scrolled across the LCD.
- Green, Yellow and Red LEDs indicate train status.
- The buzzer provides an alert when a train is approaching.
- Admin Mode temporarily takes control of the normal display when the external interrupt is triggered.

---

## 🛠️ Development

**Microcontroller:** LPC2148  
**Architecture:** ARM7TDMI-S  
**Programming Language:** Embedded C  
**IDE:** Keil µVision  
**Programming Tool:** Flash Magic

---

## ⭐ Project Highlights

> Real-Time • Informative • Efficient • Modular

The project combines RTC-based scheduling, train information management, keypad input, LCD interfacing, external interrupt handling, LED status indication, buzzer alerts and administrative validation into a single railway platform monitoring system.

---
