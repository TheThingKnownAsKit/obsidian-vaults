# Task Requirements
## Task 1
1. Create a blue LED at the beginning of setup()
2. Configure the Generic Clock Controller
	1. Type 2
	2. Frequency of 2048Hz
3. Set up the WDT
	1. Period of 2 seconds
4. Observe LED behavior

## Task 2
1. Create a blue LED at the beginning of setup()
2. Configure the Generic Clock Controller
	1. Type 2
	2. Frequency of 2048Hz
3. Set up the WDT
	1. Period of 4 seconds
4. Create a loop in loop() that continually counts down from 10 and prints "Countdown " + the current countdown num to the serial monitor.
	1. Period of 1 second
5. Case 1:
	1. Inside the countdown loop, clear the WDT
6. Case 2:
	1. Inside the countdown loop, do NOT clear the WDT

## Task 3
1. Write a function named setWatchdog above setup()
	1. Return int register_value
	2. Accept int period as a parameter
	3. Based on the given period, determine what the register_value for the WDT period should be
2. Create a blue LED at the beginning of setup()
3. Configure the Generic Clock Controller
	1. Type 2
	2. Frequency 2048Hz
4. Set up the WDT
	2. Call the function setWatchdog(period) in the command `WDT->CONFIG.bit.PER = period;` to set the period. The input should be in milliseconds
5. Observe LED behavior
	
## Task 4:
1. Consult the Atmel SAMD21G datasheet to determine if there is a way to detect the cause of the last reset
	1. If it was due to WDT, print
2. If it is not possible, explain why
# Development Plan
## LED Development
Use the examples given in the "Hello World" with embedded systems: Blinking LED section of the pdf to do this. This would be:
   `pinMode(PIN_LED_13, OUTPUT);`
   `digitalWrite(PIN_LED_13, HIGH);`

## Generic Clock Controller Development
Reference the example code given in "The procedure for setting up the WDT".
Use the command `GCLK->GENCTRL.reg = GCLK_GENDIV_ID(2)` to set a generic clock generator 2.
To configure the GCLK to 2048Hz, determine the divisor and frequency equation using the example provided and the equation. When the correct divisor for 2048Hz is found, put this information into the example code provided.
	Equation: $Frequency=\frac{32,000}{2^{DIV+1}}$
	Since the desired frequency is 2048, the equation is $2048=\frac{32,000}{2^{DIV+1}}$ which roughly solves to DIV = 3.

## Watchdog Setup Development
Process for setting up the WDT:
* Disable before configuring by using `WDT->CTRL.reg = 0;`
* Consult table 4 in section 17.8.2 to determine the correct period value for a 2 second timer on a 2048Hz clock.
![[Pasted image 20231101174251.png]]
				Because the clock is set to 2048Hz, it runs through 2048 clock cycles per second. A one second period would therefore be 8, and a two second period would be 9.
* Observe LED behavior. The LED should blink in two second intervals.

## Loop in loop() Development
Because I both a. want to know what iteration of the loop I am on and b. have a known amount of times I will loop, I should use a for loop. Because the loop will be counting DOWN, the loop variable should start at 10 and decrease by one every loop. The loop will continue as long as the loop variable is greater than 0.
	`for (int i = 10; i > 0; i--) {...}`
To clear the WDT in the loop, reference the earlier section in the lab where it gave common WDT commands. For case 2, comment out this line using //.
	`WDT->CLEAR.reg = WDT_CLEAR_CLEAR_KEY;`
I also want to print the current countdown to the serial monitor every loop. To do so, use the example code given in the task.
	`SerialUSB.print("Countdown ");`
	`SerialUSB.println(i);`
The loop should have a period of one second. Use the delay command given in the task to do so. `delay()` is in milliseconds.
	`delay(1000);`

## setWatchdog() Development
The majority of the function code is given by the task instructions. Implement this code.
```
int setWatchdog(int period)
{
// your code
return register_value;
}
```
In // your code, implement logic to determine the correct register value for the desired period. Note that the program is in 2048Hz. Because of this, the only possible time values are 1, 2, 4, and 8 seconds. Implement a switch statement that assigns register_value the appropriate number given period. Remember that one second is register 8, and each integer increase will double the period. It would make the code easier to understand to convert from milliseconds to seconds by dividing by 1000. If period is less than one second or more than 8 seconds, floor to register values 8 and 11 respectively.
Replace the usual `WDT->CONFIG.bit.PER = period;` command in setup() with `WDT->CONFIG.bit.PER = setWatchdog(period);`. Manually change period to experiment with different times. Period is in milliseconds.

## Reset Cause Development
The datasheet is 1111 pages long so I'm not scrolling through the whole thing. Think about what resetting is related to and use the left hand menu to check appropriate sections. If one is found, go through the register summary to see how to implement it.
Ask for help because I'm going to need it.
# Test Plan
## Testing the blue LED
Firstly, make sure the LED is actually the color blue. Secondly, use the stopwatch setting on phone's clock app to see if the timer is accurately set to 2 seconds.

## Testing the Watchdog Period
This one will go hand in hand with testing the blue LED. The LED is a signal for when the system resets. If the LED blinks every ~2 seconds, the period is correct. Consult table 4 in section 17.8.2 of the Atmel datasheet.

## Testing the Generic Clock Controller
The equation is already provided, so it's just a matter of making sure that whatever divisor you put into the equation gives a result of ~2000.
# Results
## Task 1
The LED was the correct color and the program reset roughly every ~2 seconds. The timing was usually off by 0.3-0.4 extra seconds. 

Generic clock configure code:
```
// Generic clock generator 2, divisor = 16
GCLK->GENDIV.reg = GCLK_GENDIV_ID(2) | GCLK_GENDIV_DIV(3);
// 2048Hz(ish) clock
GCLK->GENCTRL.reg = GCLK_GENCTRL_ID(2) |
					GCLK_GENCTRL_GENEN |
					GCLK_GENCTRL_SRC_OSCULP32K |
					GCLK_GENCTRL_DIVSEL;

GCLK->CLKCTRL.reg = GCLK_CLKCTRL_ID_WDT |
					GCLK_CLKCTRL_CLKEN |
					GCLK_CLKCTRL_GEN_GCLK2;
```

Watchdog configure code:
```
// Disable WDT before configuring
WDT->CTRL.reg = 0;

// Configure. Reference table 4 in section 17.8.2
WDT->CONFIG.bit.PER = 9;

// Enable
WDT->CTRL.bit.ENABLE = 1;
```
## Task 2
**Case 1:**
The blue LED would continuously stay on.

The program would countdown from 10->1 by printing to serial monitor and reset at 0. It looped infinitely since the WDT was getting cleared in every loop so the program was never reset. With a loop period of 1 second and a WDT period of 4 seconds, the loop would never exceed the WDT timer.

loop() code:
```
for (int i = 10; i > 0; i--) {
    WDT->CLEAR.reg = WDT_CLEAR_CLEAR_KEY;

    SerialUSB.print("Countdown ");
    SerialUSB.println(i);

    delay(1000);
  }
```

**Case 2:**
Without clearing the WDT, the program would reset every ~4 seconds. Similarly, it averaged an extra 0.3-0.4 seconds.
The blue LED would reset in this time interval.

The countdown now starts at 9, counts down to 7, and then resets back to 9. I am unsure why it starts at 9, but the countdown itself stays in the time interval as the rest of the program. 

**Overall:**
This demonstrated the importance of having a WDT in the first place.
In the first case, the WDT was improperly used to the point it was useless. Because of this, the program would loop infinitely unless I manually reset it.
In the second case, the WDT was properly utilized to ensure the program would not loop infintely.

loop() code:
```
for (int i = 10; i > 0; i--) {
    SerialUSB.print("Countdown ");
    SerialUSB.println(i);

    delay(1000);
  }
```

## Task 3
This sketch functions similarly to task 1. The blue LED blinks at certain time intervals which indicates the WDT period. The time period still averages 0.3-0.4 extra seconds.

This time period is now adjustable with a `setWatchdog(periodInMilliseconds)` function that returns a register value. `WDT->CONFIG.bit.PER = setWatchdog(periodInMilliseconds);`

It is very difficult to get a precise WDT period. Firstly, I'm unsure if it's possible to get different periods than 1, 2, 4, and 8 seconds in a 2048Hz clock. Secondly, the period will not be 100% accurate, especially on cheaper equipment. This won't always be an issue, however, because the WDT is a failsafe that triggers if too much time has passed. As long as WDT clears are used cautiously, if the WDT overshoots by a few seconds it will most likely not be a big deal. There are exceptions to this, but for the most part I can't see it being absolutely necessary.

setWatchdog() code:
```
int setWatchdog(int period) {
	// Convert from milliseconds to seconds
	period /= 1000;
	int register_value;
	
	// Assuming 2048Hz clock
	// Ranges from 1-8 seconds. Seconds doube with every integer // period increase. Floor unmappable values
	
	switch (period) {
	    case 1:
	      register_value = 8;
	      break;
	    case 2:
	      register_value = 9;
	      break;
	    case 3:
	    case 4:
	      register_value = 10;
	      break;
	    default:
	      if (period <= 0) {
	        register_value = 8;
	      } else {
	        register_value = 11;
	      }
	      break;
	  }
	  
	  return register_value;
  }
```

## Task 4
There is a way for the MCU to determine the cause of a reset. I had to ask for help. Under the PM - Power Manager category in the SAMD21 datasheet. I can use the register `RCAUSE` to determine this.

I ran into an issue implementing it because you can't just put `PM->RCAUSE.reg.WDT` otherwise it will cause a compilation error. I am unsure why this is.
The working line I ended up with was:
`SerialUSB.println(PM->RCAUSE.reg & PM_RCAUSE_WDT);`
This repeatedly printed 32 to the serial monitor. ![[Pasted image 20231102152312.png]]
