1. programmer is a hardware device which helps us upload code without a bootloader if bootloader is present we can upload it through spi i2c anything
2. bluepill- ardunio like
3. discovery -built in programmer
4. nucleo- built in programmer also has arduino pins
5. eval boards - most highend overkill

ARM Cortex M is a family of microprocessors used for embedded application it has their own instruction set and different boards using same mp can be compiled in the same way as the assembly is same

same compiler for different boards as same microporcessor

## Registers and HALS

## What is Memory-Mapped I/O?

**Memory-Mapped I/O** is a way of controlling hardware peripherals by assigning them specific memory addresses.

Basically:

> “You control hardware just by reading from or writing to specific memory addresses.”
> 

Your CPU sees **peripherals** (like GPIO, UART, SPI, etc.) as if they were **variables** in memory — but those addresses are actually connected to hardware logic, not RAM.

1.  In STM32, **registers** are **memory-mapped hardware control points**. They are special memory addresses that let your code **communicate directly with the microcontroller’s hardware** — like GPIO, timers, USART, ADC, etc.
2. GPIOA_ODR **Function:** The `GPIOA_ODR` is a register specifically used to **control the output state** (HIGH or LOW) ofis the pins belonging to GPIO Port A *when those pins are configured as outputs*.
3. when we write something into the registers it is refelcted 100101010 sets pins accdingly
4. PORTS ARE A COLLECTION OF PINS
5. PINS ARE THE ACTUAL ACUATING POINTS

## Hadware abstraction layer

instead to writing binary to register we can use a HAL

The **HAL is a software layer that hides the low-level details** of the hardware, making your code easier to write and more portable.

Arduino ide is an hal

![image.png](attachment:48717aef-4d68-4056-85a7-ff9f75bdd6c9:image.png)

IN arduino pin 3 is actully just an alias FOR PORTD pin3 
EVERY TIME WE NEED TO TURN ON OR OFF WE NEED THE PORT AS WELL AS PIN

[]()

 This makes it slow whereas the stm hal doesnt need processing 

![image.png](attachment:c812c072-43f3-4be9-80a9-2cc8c136e9e7:image.png)

workflow

1. Configure pins of stm32 
2. write code and compile
3. flash and debug that is what each part is doing
it is all integrated now

### **MCU/MPU Selector**

- Lets **you choose a specific STM32 chip** (e.g., `STM32F103C8T6`, `STM32H743ZI`, etc.)
- Good if you **know exactly** which microcontroller you're using.
- You'll configure all the pins, clocks, peripherals from scratch (or with templates).

✅ Use this if:

- You’re working on a **custom board**

### 🧩 **Board Selector**

- Lets you pick from a list of **ST’s official dev boards** (e.g., `NUCLEO-F103RB`, `STM32F4-Discovery`, etc.)
- STM32CubeIDE **auto-configures** everything (like clocks and pins) to match that board.

✅ Use this if:

- You're using an **ST development board\**
- blue button is connectoned to pin 13 so it configures it accordingly

# building

after making a new project we need to configure pins to output input etc

just for inital configuration we can change the config in the code as well

1. clock if dont chnage uses builtin oscillator
2. then generate code

![image.png](attachment:0d92e74b-023c-4d8c-b987-de0a924ca277:image.png)

only code between the comments becuse if we change the config the things not in comments will dissapear

each port has a register and each binary is a pin on it which controls high low

IN THE BLUEPILL MODE U NEED THE PROGRAMMER FIRST CONNECT IT THEN CONNECT JUMPER /STRAPPING PINS TO CHNAGE IT TO UPLOAD MODE THEN TO RUN MODE