# STM32-PushButton-LED-Control-Using-GPIO
STM32F446RE GPIO interfacing project demonstrating push button input handling and onboard LED state toggling using HAL GPIO functions and software debouncing in STM32CubeIDE.

---

## Overview

This project demonstrates how to interface a push button as a digital input and control the onboard LED by toggling its state on each valid button press.

The onboard user button connected to PC13 is used as an input, while the onboard LED connected to PA5 is configured as a digital output.

The project is developed using:

- STM32CubeMX
- STM32CubeIDE
- STM32 HAL Library

---

## Features

- GPIO input configuration
- GPIO output configuration
- Push button interfacing
- LED toggle operation
- Software debouncing
- STM32 HAL-based implementation

---

## Hardware Requirements

- STM32 Nucleo-F446RE Development Board
- USB Type-A to Mini-B Cable

---

## Software Requirements

- STM32CubeIDE
- STM32CubeMX

---

## GPIO Configuration

| GPIO Pin | Configuration |
|------------|----------------|
| PA5 | GPIO Output (Onboard LED LD2) |
| PC13 | GPIO Input (User Push Button) |

---

## Working Principle

The onboard push button connected to PC13 is continuously monitored inside the infinite loop.

When the button is pressed:

1. The input pin state becomes LOW
2. The LED state toggles
3. A software delay is applied for debouncing
4. The LED maintains its new state after button release

---

## Source Code

```c
while (1)
{
    // Read onboard button (PC13)

    if (HAL_GPIO_ReadPin(GPIOC,
                         GPIO_PIN_13) == 0)
    {
        // Toggle LED

        HAL_GPIO_TogglePin(GPIOA,
                           GPIO_PIN_5);

        // Simple debounce delay

        HAL_Delay(200);
    }
}
```

---

## Build and Run

1. Open the project in STM32CubeIDE
2. Configure GPIO pins using STM32CubeMX
3. Build the project
4. Connect STM32 board via USB
5. Flash the firmware to the board
6. Run the program

---

## Expected Output

- Pressing the push button toggles the onboard LED
- LED state remains unchanged after button release
- Every valid button press changes the LED state

---

## Observation

| Action | LED Response |
|---------|---------------|
| First Press | LED toggles |
| Second Press | LED toggles again |
| Rapid Press | Controlled using debounce delay |

---

## Learning Outcomes

- Understanding GPIO input/output configuration
- Push button interfacing
- LED control using GPIO
- Software debouncing
- STM32 HAL functions
- Embedded systems programming basics

---

## Future Improvements

- Implement interrupt-based button handling
- Add multiple button support
- Use timer-based debouncing
- Integrate PWM LED control
- Add RTOS-based task handling

---

## Author

**Ayush Jangra**  
ECE Student | Chitkara University

---

## License

This project is created for educational and academic purposes.
