## WATCHDOG TIMER (WDT) INTRODUCTION
The ***Watchdog Timer*** (WDT) is a system function for monitoring correct program operation. Essentially, it's a timer that runs during a program's execution. If the timer ever exceeds a configured threshold, the program will be reset. It makes it possible to recover from error situations such as runaway or deadlocked code.

![[WDTDiagram.png]]

1. Hardware counter that counts down from an initial value (timeout interval) to zero.
2. A mechanism to detect when the processor has hung.
3. Can automatically recover the system from crash or hung without intervention.
4. If count reaches zero, it resets the processor (not necessarily the peripherals).
5. To prevent resets, application software kicks (resets) the watchdog.

## SETTING UP THE WATCHDOG
The WDT is configured to a predefined time-out period and is constantly running when enabled. If the WDT is not cleared within the time-out period, it will issue a system reset.

Components of the WDT include:
1. Source clock
	1. The clock used to count down
2. Watchdog reset period
3. Interrupt

To begin the configuration process,
1. Find out what registers will be needed (By reading the SAMD21 Datasheet)
	1. https://cdn.sparkfun.com/assets/6/3/d/d/2/Atmel-42181-SAM-D21_Datasheet.pdf
2. Map the register address to code (Automatically done by Arduino Core)
3. Configure the related registers (Code)
See Section 17.6 of the SAMD21 datasheet for details.

Next, you need to configure the clock source. To do so, you will need to select the clock source and configure source clock frequency.
	See Section 14.8.3 of the SAMD21 datasheet for details.

For now, you will be using a clock generator 2 as your source clock. To determine the frequency, you will need to use the equation below to determine the divisor to put into the configuration.
$frequency(Hz)=\frac{32000}{2^{DIV+1}}$

Example code for how to create a source clock and assign it to the WDT:
```C++
// Generic clock generator 2, frequency = 32000/(2^(DIV + 1))

GCLK->GENDIV.reg = GCLK_GENDIV_ID(2) | GCLK_GENDIV_DIV(5);
// Enable clock generator 2 using low-power 32KHz oscillator.
// With /64 divisor above, this yields 512Hz(ish) clock.
GCLK->GENCTRL.reg = GCLK_GENCTRL_ID(2) |
					GCLK_GENCTRL_GENEN |
					GCLK_GENCTRL_SRC_OSCULP32K |
					GCLK_GENCTRL_DIVSEL;
while (GCLK->STATUS.bit.SYNCBUSY); // Think about why this is used

// WDT clock = clock gen 2
GCLK->CLKCTRL.reg = GCLK_CLKCTRL_ID_WDT |
					GCLK_CLKCTRL_CLKEN |
					GCLK_CLKCTRL_GEN_GCLK2;
```

Configure the WDT:
```C++
WDT->CONFIG.bit.PER = period;       // Set period for chip reset from the datasheet
WDT->INTENCLR.bit.EW = 1;           // Disable early warning interrupt
WDT->CTRL.bit.WEN = 0;              // Disable window mode
```

## IMPORTANT WDT FUNCTIONS
***Sync Busy***:
When executing an operation that requires synchronization, the Synchronization Busy bit in the Status register (`STATUS.bit.SYNCBUSY`) will be set immediately, and cleared when synchronization is complete. Some processes require you to wait for synchronization before proceeding.

Use this code to wait for synchronization:
`while(GCLK->STATUS.bit.SYNCBUSY`

 ***Enable/Disable***:
To enable the WDT:
`WDT->CTRL.bit.ENABLE = 1;`

To disable the WDT:
`WDT->CTRL.reg = 0;`

NOTE: You NEED to disable the WDT during configuration to prevent run-time changes to the registers.

***Clear***:
Clearing the WDT, or kicking, prevents it from resetting and keeps your program running.
`WDT->CLEAR.reg = WDT_CLEAR_CLEAR_KEY;`

## ASSIGNMENT: WATCHDOG
**Please note that the information provided in Setting Up the Watchdog is incomplete.** You will need to consult the SAMD21 datasheet to fill in the blanks and complete the tasks. The purpose of this lab is to not only teach you how to use a WDT, but also how to navigate the Arduino IDE and the SAMD21 datasheet.

While completing the tasks for this lab and all future labs, you are expected to follow a development plan and testing procedures. See the deliverables section to read these requirements. The expected deliverables will change every lab so you should review them before beginning all assignment.

**Learning Objectives:**
* Reading microcontroller datasheet:
	* SparkFun PRO RF Graphical datasheet: https://cdn.sparkfun.com/assets/e/0/6/6/5/SamProRF_Graphical_Datasheet_Updated.pdf
	* SAMD21G Datasheet: https://cdn.sparkfun.com/assets/6/3/d/d/2/Atmel-42181-SAM-D21_Datasheet.pdf
* Understand registers and how to enable registers in Arduino
* Learn the importance of a watchdog timer

### Tasks
#### Task 1 (20 points)
* Set up a WDT that resets without clearing it
	* Set the Blue LED at the beginning of the program
	* Create a Clock (clock generator 2) with a frequency of 2048Hz
	* Set WDT period to 2 seconds
	* Observe the behavior of the blue LED
	* Do nothing in the main loop()

<br>

#### Task 2 (20 points)
* **Case A:** Set up a loop that clears the WDT
	* Set the Blue LED at the beginning of the program
	* Create a Clock (clock generator 2) with a frequency of 2048Hz
	* In the main loop() function such that it:
	* Set the WDT period to 4 seconds
		* Loops 10 times
		* Has a loop period of 1 second (using the delay function)
		* Kicks the WDT in the loop
		* Counts down the number of loops and prints the countdown to the serial monitor. For example:
```C++
SerialUSB.print("Countdown ");
SerialUSB.print(number);
```
Output:
```
Countdown 9
Countdown 8
```

**Case B:** Try it again without clearing the WDT by commenting the corresponding lines
* Compare the difference between the cases 1) with clearing the WDT, and 2) without clearing the WDT.
* Record the system, LED, and serial monitor behavior.

**Question:** Discuss and explain the differences between the two cases.

#### Task 3 (10 points)
* Write a function that generates the WDT period by arbitrary input and implement it into Task 1's scenario
	* Create a Clock (clock generator 2) with a frequency of 2048Hz
	* Create a function named input:
		* Accepts a parameter named period (time in milliseconds)
		* Calculate the register value based on the period
		* For values that cannot be mapped to register value, take closest value

Example function:
<br>
<br>
```C++
int setWatchdog(int period)
{
	// your code
	return register_value;
}

// Utilize this function using WDT->CONFIG.bit.PER = setWatchdog(period);
```
<br>

**Questions:**
* How to get an accurate WDT period?
* Is it necessary to use an accurate period?

#### Task 4 (10 points) (838: Required, 438: Bonus points)
After a reset, there is a way for the MCU to figure out if the last reset was due to the WDT. To familiarize yourself with how to search through the SAMD21 datasheet, determine the correct register to utilize and implement it into Task 1A's scenario.

* Write code that detects if the last reset was due to a WDT.
* If it was, print a message in console.
* Describe the importance of knowing the reset cause.

Hint: If you're having difficulty finding the correct section in the datasheet, it can be useful to think about what system manages resets.

### Report
1. The requirements for each task
2. Development plan
	1. The procedure of solving the problem
	2. The configurations used for each task
3. Test plan
4. Results
	1. Answer the questions following each task
	2. Code snippets for each function
	3. Figures in the report:
		1. Screenshots that show you completed the required functions (serial message and Arduino IDE warning)
		2. Pictures that show you completed the required functions if necessary
	4. Test results
		1. For example, varying the WDT period to see how results change

**Program**
Your Arduino sketch(s) in the appendix.

### Submission Instructions
1. Submit your lab on Canvas on or before the deadline.
2. Your submission should include one single PDF explaining everything that was asked in the tasks and screenshots, if any.
3. Your submission should also include all the code that you have worked on with proper documentation (Do not attach your code separately as an .ino file. Instead, copy and paste your code in the Appendix. Do not use screenshots in the Appendix.).
4. Failing to follow the instructions will make you lose points.

## REFERENCES
1. SparkFun SAMD21 Pro RF Hookup Guide: https://learn.sparkfun.com/tutorials/sparkfun-samd21-pro-rf-hookup-guide?_ga=2.127628877.1139230921.1561643965-144910588.1557512622#setting-up-arduino
2. SparkFun Pro RF Documentation: https://www.sparkfun.com/products/14916