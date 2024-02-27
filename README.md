# STM32 Blue Pill OS Scheduler

## Overview

This project implements an OS Scheduler in C for the STM32 Blue Pill microcontroller. It allows scheduling one-shot or periodic tasks with configurable parameters.

## Usage

1. Clone the repository:

git clone https://github.com/Mohamedahmed2k/OS-Scheduler.git

scss
Copy code

2. Configure the project according to your requirements.
3. Build the project using your preferred toolchain.
4. Flash the compiled binary onto your STM32 Blue Pill microcontroller.

## Configuration

- Define the number of tasks and configure each task with its first call time and period time in `OS_interface.h`.
- Adjust microcontroller settings such as clock frequency, GPIO configurations, etc., in the provided configuration files.

## Example

```c
#include "OS_interface.h"

void LED1(void);
void LED2(void);
void LED3(void);

void main()
{
 RCC_voidInitSysClock();
 RCC_voidEnableClock(RCC_APB2,2);
 GPIO_voidSetPinMode(GPIO_PORTA,0,0b0100);
 GPIO_voidSetPinMode(GPIO_PORTA,1,0b0010);
 GPIO_voidSetPinMode(GPIO_PORTA,2,0b0010);
 GPIO_voidSetPinMode(GPIO_PORTA,3,0b0010);
 SOS_voidCreateTask(0,1000 , LED1 , 0);
 SOS_voidCreateTask(1,5000 , LED2 , 1);
 SOS_voidCreateTask(2,10000 , LED3 , 2);
 SOS_voidStart();
 while(1)
 {

 }
}

void LED1(void)
{
 static u8 Local_u8Pin1 = 0 ;
 TOG_BIT(Local_u8Pin1 , 0);
 GPIO_voidSetPinValue(GPIO_PORTA,GPIO_PIN3,Local_u8Pin1);

}
void LED2(void)
{
 static u8 Local_u8Pin2 = 0 ;
 TOG_BIT(Local_u8Pin2 , 0);
 GPIO_voidSetPinValue(GPIO_PORTA,GPIO_PIN1,Local_u8Pin2);

}
void LED3(void)
{
 static u8 Local_u8Pin3 = 0 ;
 TOG_BIT(Local_u8Pin3 , 0);
 GPIO_voidSetPinValue(GPIO_PORTA,GPIO_PIN2,Local_u8Pin3);

}


```
## Configuration

- Define the number of tasks and configure each task with its first call time and period time in `OS_interface.h`.
- Adjust microcontroller settings such as clock frequency, GPIO configurations, etc., in the provided configuration files.

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
---
Feel free to further customize the README.md file to include more details or specific instructions as needed.





 
