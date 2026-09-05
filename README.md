# Smart-Railway-Platform-Clock-Announcement-Controller

An embedded railway platform monitoring system designed to display real-time information and automatically monitor train schedules using an RTC, LCD, keypad, LEDs, buzzer, and external interrupt.

## Features

- Real-time date and time display
- Automatic train schedule monitoring
- Upcoming train information display
- Scrolling display for train information
- LED indication for different train conditions
- Buzzer indication for approaching trains
- Admin mode using external interrupt
- PIN-based admin authentication
- RTC date and time modification
- Train schedule modification
- Input validation
- Platform conflict checking

## Hardware Used

- ARM7 Microcontroller
- 16x2 LCD
- 4x4 Matrix Keypad
- RTC
- LEDs
- Buzzer
- Push Button / Switch

## Project Flow

The system starts by initializing all the required peripherals such as the LCD, RTC, keypad, indicators, and external interrupt.

After initialization, the RTC provides the current date and time. The system continuously compares the current time with the stored train schedule.

When a train is approaching, its information is displayed on the LCD and the required LED and buzzer indications are activated.

If no train is approaching, the system continues displaying the normal railway information.

An external interrupt is used to enter **Admin Mode**, where authorized changes can be made to the system settings.

## Normal Mode

1. Initialize the required hardware peripherals.
2. Read the current date and time from the RTC.
3. Continuously monitor the train schedules.
4. Check whether any train is approaching.
5. Display the approaching train information on the LCD.
6. Provide LED and buzzer indications when required.
7. Display normal information when there is no approaching train.
8. Continue monitoring until Admin Mode is requested.

## Admin Mode

1. The push button generates an external interrupt.
2. The interrupt service routine activates Admin Mode.
3. The admin menu is displayed on the LCD.
4. PIN authentication is performed.
5. The administrator can modify the required settings.
6. Entered values are checked for validity.
7. Platform conflicts are checked before saving.
8. Valid changes are saved.
9. The system returns to Normal Mode.

## Software Modules

- `train_main.c` – Main program and overall system flow
- `RTC.c` – RTC initialization and date/time handling
- `lcd.c` – LCD interfacing
- `keypad.c` – Keypad interfacing
- `interrupt.c` – External interrupt handling
- `indicator.c` – LED and buzzer control
- `admin.c` – Admin menu and data modification
- `train_dprint.c` – Train information display
- `railway.c` – Railway schedule data
- `delay.c` – Delay functions

## Project Type

**Embedded Systems / ARM7 / Real-Time Railway Monitoring**
