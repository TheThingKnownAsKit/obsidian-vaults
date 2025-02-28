SamProRF Graphical Datasheet:
https://cdn.sparkfun.com/assets/e/0/6/6/5/SamProRF_Graphical_Datasheet_Updated.pdf

SAMD21G datasheet:
https://cdn.sparkfun.com/assets/6/3/d/d/2/Atmel-42181-SAM-D21_Datasheet.pdf

# Basic Info
Arduino software (aka *sketch*) includes two main parts: `Setup()` and `Loop()`.
* `Setup()`
	* Defines initial state of the Arduino upon boot and runs only once.
	* Do the following:
		* Pin functionality using pinMode function
		* Initialize the state of pins
		* Initialize classes
		* Initialize variables
		* Initialize hardware (timer/serial/etc.)
* `Loop()`
	* Executes once setup is complete.
	* It is the main function and runs over and over again.
	* Main logic of the circuit.

# Watchdog
## Watchdog Timer (WDT)
The *Watchdog Timer (WDT)* is a system function for monitoring correct program operation. It makes it possible to recover from error situations such as runaway or deadlocked code.
![[Pasted image 20231026180635.png]]
1. Hardware counter that counts down from an initial value (timeout interval) to zero
2. A mechanism to detect when the processor has hung
3. Can automatically recover the system from crash or hung without intervention
4. If count reaches zero, it resets the processor (not necessarily the peripherals!)
5. To prevent resets, application software kicks (or pets) the watchdog

It has a time-out period and is constantly running when enabled. If the WDT is not cleared within the time-out period, it will issue a system reset.

## Watchdog Configurations
General:
1. Source clock
	1. Watchdog uses clock to count down
2. Watchdog reset period
3. Interrupt

Special config of SAMD21 watchdog (not required)
1. Window
2. Pre-interrupt warning

## Watchdog Functions
Note: When executing an operation that requires synchronization (writing Control or Clear register), the Synchronization Busy bit in the Status register (STATUS.SYNCBUSY) will be set immediately, and cleared when sync is complete. Use this line to wait for synchronization
`while(GCLK->STATUS.bit.SYNCBUSY);`

General functions:
* Enable
	* Enable the WDT in the microcontroller
`WDT->CTRL.bit.ENABLE = 1;`
* Disable
	* Disable the WDT to set up configuration to prevent run-time changes to the registers
`WDT->CTRL.reg = 0; // Disable watchdog for config`
* Clear
	* Clearing the WDT, which also means kicking the WDT, prevents the WDT from resetting and keep your program running
`WDT->CLEAR.reg = WDT_CLEAR_CLEAR_KEY;`

## The procedure for setting up the WDT
1. Find out the registers needed (By reading datasheet)
2. Map the register address to code (Done by Arduino Core)
3. Configure the related registers (Code)
   See Section 17.6 of the SAMD21 datasheet for details.

* Configuration of the clock source
	* First select the clock source and configure source clock frequency
	  See Section 14.8.3 of the SAMD21 datasheet and the Clock Timing Math subsection
```
// Generic clock generator 2, divisor = 32 (2^(DIV + 1))

GCLK->GENDIV.reg = GCLK_GENDIV_ID(2) | GCLK_GENDIV_DIV(5);
// Enable clock generator 2 using low-power 32KHz oscillator.
// With /64 divisor above, this yields 512Hz(ish) clock.
GCLK->GENCTRL.reg = GCLK_GENCTRL_ID(2) |
					GCLK_GENCTRL_GENEN |
					GCLK_GENCTRL_SRC_OSCULP32K |
					GCLK_GENCTRL_DIVSEL;
while(GCLK->STATUS.bit.SYNCBUSY); // Need to wait for synchronization
// WDT clock = clock gen 2
GCLK->CLKCTRL.reg = GCLK_CLKCTRL_ID_WDT |
					GCLK_CLKCTRL_CLKEN |
					GCLK_CLKCTRL_GEN_GCLK2;
```
* Disable the WDT before configuring it
* Then you need to initiate the period of your watchdog and other configurations
```
WDT->CONFIG.bit.PER   = <period>; // Set period for reset from the datasheet
WDT->INTENCLR.bit.EW  = 1;        // Disable early warning interrupt
WDT->CTRL.bit.WEN     = 0;        // Disable window mode
```
* Enable the WDT
	* You can clear it but don't disable it

##### Clock Timing Math
$\frac{32,000}{2^{Div + 1}}=Clock Freq$
32k is the internal clock. It's the only clock in the system, and 32k is REALLY fast so you have to limit it to a more reasonable speed.

$\frac{32,000}{2^{5 + 1}}=500Hz$
Every one second will be 508Hz.
The div will be put in `GCLK_GENDIV_DIV(DIVISIOR)`

This information is also needed to configure the period. The period is not a number, it's a register. Based on the desired number of seconds and the frequency of the clock. Refer to section 17.8.2 Table 17-4 for the times.
![[Pasted image 20231031152111.png]]
So, if you want your period to be 2 seconds and your clock is running on 508Hz, you will set the period to 7 for ~2 seconds.
	Noticed that the divisor is just the period - 1.
# Interrupt
**Interrupt:** Input signal to the processor indicating an event that needs immediate attention. These warnings are then processed and suitable responses are given. The processor stops the program, handles the interrupt, and then resumes.
* Timers can generate interrupts:
	* **Counter Overflow/Underflow: OVF.** An asynchronous interrupt and can be used to wake-up the device from any sleep mode
	* **Compare or Capture Channel: MCx.** Asynchronous interrupt that can be used to wake-up the device from any sleep mode
	* **Compare Overflow Error: ERR.** Asynchronous interrupt that can be used to wake-up the device from any sleep mode.
	* **Asynchronization Ready: SYNCRDY.** Asynchronous interrupt and can be used to wake-up the device from any sleep mode
	* Generate periodical events/waveforms
	* See Timer Mode for modes
	* Interrupts are ranked by emergency. With maskable interrupts being overwrittenable and Non-maskable interrupt (NMI) not being overwrittenable

Functions: Section 29.6 on datasheet
* **Interrupt-Handling Startup**: Initialization of the interrupt hardware upon power-on or reset
* **Interrupt-Handling Shutdown**: Configuring interrupt hardware into its power-off state
* **Interrupt-Handling Disable**: Allows other software to disable active interrupts on-the-fly (not for NMIs)
* **Interrupt-Handling Enable**: Allows other software to enable inactive interrupts on-the-fly
* **Interrupt-Handler Servicing**: The interrupt-handling code itself, which is executed after the interruption of the main execution stream

Registers: Section 29.7-29.8 on datasheet

## Timer Mode:
**Timer Waveform Generation Operation/Frequency Operation Mode**
1. **Normal Frequency Operation (NFRQ)**: 
	* When used, the waveform output (WO[x]) toggles every time *CCx and the counter are equal*, and the interrupt flag corresponding to that channel will be set. The top value is the maximum value allowed.
	![[Pasted image 20231102155902.png]]
2. **Match Frequency Operation (MFRQ)**:
	* When used, the value in *CC0 will be used as the top value* and WO[0] will toggle on every overflow/underflow.
	![[Pasted image 20231102160042.png]]
## Simple Timer Examples
Don't use `delay()`. It monopolies the processor. Use `millis()` instead. It returns the number of milliseconds passed since the Arduino began running the current program.
You can also use Timer Interrupt

These examples show how to use the microcontrollers to do periodical tasks. This allows for multi-tasking.
### Simple timer using millis():
```
// LED definitions in the datasheet
// D13 (PIN_LED_13): Blue
// TX (PIN_LED_TXL): Green
// RX (PIN_LED_RXL): Yellow
// Variables will change:
long previousMillis = 0; // will store last time LED was updated

// the follow variables is a long because the time, measured in miliseconds,
// will quickly become a bigger number than can be stored in an int.
long interval = 1000; // interval at which to blink (milliseconds)

void setup() {
	// set the digital pin as output:
	pinMode(PIN_LED_13, OUTPUT);
}
	
void loop() {
	// here is where you'd put code that needs to be running all the time.
	unsigned long currentMillis = millis();
	
	if(currentMillis - previousMillis > interval) {
	// save the last time you blinked the LED
	previousMillis = currentMillis;
	
	// Do something here
	}
}
```

### Simple Timer using Timer Interrupt:
```
// LED definitions in the datasheet
// D13 (PIN_LED_13): Blue
// TX (PIN_LED_TXL): Green
// RX (PIN_LED_RXL): Yellow

#define CPU_HZ 48000000
#define TIMER_PRESCALER_DIV 1024

void startTimer(int frequencyHz);
void setTimerFrequency(int frequencyHz);
void TC3_Handler();

bool isLEDOn = false;

void setup() {
	SerialUSB.begin(9600);
	// while(!SerialUSB);
	pinMode(PIN_LED_13, OUTPUT);
	startTimer(1);
}

void loop() {}

void setTimerFrequency(int frequencyHz) {
	int compareValue = (CPU_HZ / (TIMER_PRESCALER_DIV * frequencyHz)) - 1;
	TcCount16* TC = (TcCount16*) TC3;
	// Make sure the count is in a proportional position to where it was
	// to prevent any jitter or disconnect when changing the compare value.
	TC->COUNT.reg = map(TC->COUNT.reg, 0, TC->CC[0].reg, 0, compareValue);
	TC->CC[0].reg = compareValue;
	SerialUSB.println(TC->COUNT.reg);
	SerialUSB.println(TC->CC[0].reg);
	while (TC->STATUS.bit.SYNCBUSY == 1);
}

void startTimer(int frequencyHz) {
	REG_GCLK_CLKCTRL = (uint16_t) (GCLK_CLKCTRL_CLKEN | GCLK_CLKCTRL_GEN_GCLK0 | GC LK_CLKCTRL_ID_TCC2_TC3) ;
	while ( GCLK->STATUS.bit.SYNCBUSY == 1 ); // wait for sync
	
	TcCount16* TC = (TcCount16*) TC3;
	
	TC->CTRLA.reg &= ~TC_CTRLA_ENABLE; //Disable timer
	while (TC->STATUS.bit.SYNCBUSY == 1); // wait for sync
	
	// Use the 16-bit timer
	TC->CTRLA.reg |= TC_CTRLA_MODE_COUNT16;
	while (TC->STATUS.bit.SYNCBUSY == 1); // wait for sync
	
	// Use match mode so that the timer counter resets when the count matches the c ompare register TC->CTRLA.reg |= TC_CTRLA_WAVEGEN_MFRQ;
	while (TC->STATUS.bit.SYNCBUSY == 1); // wait for sync
	
	// Set prescaler to 1024
	TC->CTRLA.reg |= TC_CTRLA_PRESCALER_DIV1024;
	while (TC->STATUS.bit.SYNCBUSY == 1); // wait for sync
	
	setTimerFrequency(frequencyHz);
	
	// Enable the compare interrupt
	TC->INTENSET.reg = 0;
	TC->INTENSET.bit.MC0 = 1;
	
	NVIC_EnableIRQ(TC3_IRQn);
	TC->CTRLA.reg |= TC_CTRLA_ENABLE;
	while (TC->STATUS.bit.SYNCBUSY == 1); // wait for sync
}

void TC3_Handler() {
	TcCount16* TC = (TcCount16*) TC3;
	// If this interrupt is due to the compare register matching the timer count
	// we toggle the LED.
	if (TC->INTFLAG.bit.MC0 == 1) {
		TC->INTFLAG.bit.MC0 = 1;
		// Write callback here!!!
		digitalWrite(PIN_LED_13, isLEDOn);
		isLEDOn = !isLEDOn;
	}
}
```
## SAMD21 Interrupt Controller:
**SAMD21 Nested Vector Interrupt COntroller (NVIC)**
* For timers
	* Build-in functions:
		* `NVIC_DisableIRQ(TCx_IRQn);`
		* `NVIC_ClearPendingIRQ(TCx_IRQn);`
		* `NVIC_SetPriority(TCx_IRQn, 0);`
		* `NVIC_EnableIRQ(TCx_IRQn);`
	* Interrupt service handler:
		* `void TCx_Handler()`
# Clock System
Embedded boards have an **oscillator**, which is a circuit whose sole purpose is generating a repetitive signal of some type.
* Waveforms with multiple shapes (square, sinusoidal, pulsed, sawtooth, etc)
* Because of increasing complicated microcontrollers, there are different types of clocks used together
	* **Fast clock**: drives CPU which can be started and stopped rapidly to conserve energy but does not need to be accurate.
	* **Slow clock**: Runs continuously to monitor real time, which uses little power and may need to be accurate
	* **Crystal**: Accurate, stable, high and low frequency (typically a few MHz-32kHz) for real-time clock. Expensive, delicate, large current, sometimes needs two capacitors, long startup and stabilize time.
	* **Resistor and capacitor (RC)**: Cheap, quick to start, can be external or integrated with MCU. Poor accuracy and stability. Some provide four frequency calibrations.


SQUARE OSCILLATOR:
![[Pasted image 20231102160908.png]]

## SAMD21 Clock System:
Consists of:
* Clock sources, controlled by SYSCTRL
* **Generic Clock Controller (GCLK)** which controls the clock distribution system, made up of:
	* Generic Clock generators: Programmable prescalar that can use any of the system clock sources as its source clock.
		* Generator 0, `GCLK_MAIN`, is the clock feeding the Power Manager used to generate synchronous clocks.
	* Generic Clocks: Clock input of a peripheral on the system. Can use any of the Generic Clock generators as its clock source.
		* Multiple peripherals will have their own separate generic clocks (usually)
		* The `DFLL48M` clock input (when multiplying another clock source) is generic clock 0

Clock Selection:
![[Pasted image 20231102162820.png]]

A **Waveform Generation Operation** generates new frequency signals based on the time.
## Components/Concepts/Features
Timers provide:
* Time at which transition occurs. Can be recorded
* Outputs can be driven on and off automatically at specified frequencies
* They provide a regular "tick" that can be used to schedule task in a program
	* Note that timers do not increment indefinitely. There are modes to control the frequency operation of the timer, where the top value of the time can be configured.

Components of timers:
1. **Clock source**: By using a clock source, the counter can be incremented at regular intervals
2. **Counter**: Counts the number of times that the detector signal transitions from high to low. This is a register
3. **Prescaler**: Implemented as counters in and of themselves. They can divide the system clock by a range of different divisors.
4. **Signal Selector**: A multiplexer that selects one of the available event sources to be provided to the counter. Determined by the configuration of the counter
![[Pasted image 20231102162435.png]]

Features of TC on SAMD21:
* Selectable configs
* 8-, 16-, or 32-bit TC with compare/capture channels
* Waveform generation
	* Frequency generation
	* Single-slope pulse-width modulation
* Input capture
	* Event capture
	* Frequency capture
	* Pulse-width capture
* One input event
* Interrupts/output events on:
	* Counter overflow/underflow
	* Compare match or capture
* Internal prescaler