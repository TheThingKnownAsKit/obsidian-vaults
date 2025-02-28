Files used:
`Fall_2022_-_CSCE_438_838_IoT_-_Lab_1`

## Installation/Setup
* Overall very easy to follow and informative. I only got lost a few times and for me that's impressive, especially considering this is the first time I've set up an arduino myself and I don't regularly use the command line
	* I like the pictures and links, makes it very easy
* Times I did get lost:
	* It is unclear that you need to download the SparkFun SAMD boards dependencies for the SparkFun Board Definition to work
	* I have no idea what port baud rate is and I couldn't find it anywhere in the IDE
	* For downloading the arduino-cli, the given instructions only work for mac users. Windows command line doesn't support sh commands. However, Git Bash does. I just ended up using the Git Bash command line for the rest of the instructions
	* It is unclear that you have to open the arduino-cli config file from your file system. Also, I don't know why the - is before https in the picture since it causes an error if you include it
	* When I tried to use the command `sudo arduino-cli upload -p /dev/ttyACM0 --fqbn SparkFun:samd:samd21_proRF MyFirstSketch` I was given the error that sudo is not a command
	* For the first hello world program that prints to serial monitor, it is unclear that you have to go to the tools tab to open the serial monitor. I couldn't get it to work until I went back to it later with a new idea and figured it out. The serial monitor in general isn't really explained but I'm unsure if people normally know more about the arduino IDE going into this lab

Some of the pictures are outdated and the GUI no longer looks like that. Maybe some pictures for both mac and windows computers would be helpful. I'm pretty used to translating from mac to windows and I used to have a mac so it wasn't that difficult for me, but it might be different for others.
## Lab1
### Activities
* Task 1:
	* Completed after help with the math.
	* The blue LED turned off and back on again roughly every ~2 seconds
* Task 2:
	* Case 1:
		* The program looped infinitely. It counted down from 10 every one second but when it hit 0 it would just loop back to 10. The WDT was getting kicked in every loop so it never terminated the program.
	* Case 2:
		* The program would start counting down. It started at 9 for some reason and when it hit 7 (~roughly 4 seconds) the program would shut off, turn on again, and restart from 9. This continued infinitely.
	* Question:
		* In case 1, the WDT got cleared in every loop. This essentially meant that the timer until the program was shut down got reset to 0 in every loop. Each loop was one second long, and the WDT period was 2 seconds. This meant it would continue to loop infinitely.
		* In case 2, the WDT did not get cleared. It continued to count down until it reached it's period (4 seconds), and then it would turn the program off. I am unsure why the program starts again.
* Task 3: 
	* It is difficult to get an accurate WDT period since the only mappable values for a 2048Hz clock is 1 second, 2 second, 4 second, or 8 seconds. If you want a 5 second timer, you're going to get stuck with an 8 second timer.
	* I don't think it is ALWAYS necessary to use a completely accurate period. A WDT is a failsafe for if your program runs too long. If you program it with that in mind, the time constraint probably won't be that big of a problem. However, there are probably some situations where precise timing is extremely important. I believe that you could get around some of these situations using delays or while's to pause the program.
* Task 4:
	* My best guess for the main importance of knowing the reset cause would be for debugging purposes. It is useful to know why your program stopped because this could signal if the logic is working or not.
### Notes
**Lab**
* Task 1:
	* There is a missing k and / after 32. It just looks like divisor = 32 (2^(DIV+1)) when it should be divisor = 32k/(2^(DIV+1)). This is unclear and I didn't even realize it was one equation, I thought it was saying that the divisor is 32 and they got that by using (2^(DIV+1)). $divisor=\frac{32,000}{2^{DIV+1}}$
	* It is unclear that the period of the WDT is NOT just the given number and you must consult the datasheet
* Task 4:
	* I struggled to find the register for detecting the reset cause. Maybe instead of saying "is there a way?" it could be more "there is a way, go find it". I understand why it's important to go hunting through the datasheet because you'll need to, but understanding that that's what you're supposed to do right here would've helped me feel less aimless and like I could be wasting my time.

**Overall lab takeaway:**
There were few times when I thought the instructions were unclear or I thought they were unfair. I did struggle at times but it mostly felt like places I was supposed to struggle and come to the answer by myself and with some assistance if I needed it. It wasn't an easy lab but overall didn't feel unfair or frustrating.

**Suggestions for improvement:**
I think this lab would benefit the most from just elaborating WHY more. There were several points where if I had just known why this task or subtask was here then I would have felt less lost. For example, on task 4, If I had known the purpose of this task was learning how to read the datasheet then I wouldn't have felt like I was wasting my time by combing through the sections I thought it could be in. I would've felt like I was making progress or gaining something valuable because the whole point was to comb through the datasheet.
Also a rubric for the deliverables would be nice.
## Lab 1 solution notes
While configuring the watchdog, also disable early warning interrupt and window mode
```
WDT->CTRL.reg = 0;
SerialUSB.begin(9600);
WDT->CONFIG.bit.PER = 0x09;
WDT->INTENCLR.bit.EW = 1; // interrupt disable
WDT->CTRL.bit.WEN = 0; // Disable window mode
WDT->CTRL.bit.ENABLE = 1;
```
Use the actual values given for period registers and not just the number
So 0x09 instead of just 9. I think 9 still works maybe but that's not what they did.

When writing `SetWatchdog(int period) {..}` there's actually math to it.
```
if(period <= 0){
    return 0; // Smallest period possible
  }

  int frequency = 2048;
  float cycles = (period * frequency)/1000.0;

  if (cycles > 16384){
    return 0xB; // Max period available
  }

  float wdt_period = log(cycles)/log(2) - 3; // We need log base 2 of the cycles

  if (wdt_period < 0){
    return 0;
  }

  return ceil(wdt_period); // Using ceil instead of floor as a caution
```

You can actually assign the `PM->RCAUSE.reg` to a variable. Should've used this variable in an if statement to print something other than 32.
```
int value = PM->RCAUSE.reg;
if (PM_RCAUSE_WDT & value) {
	SerialUSB.println("Last reset was caused by WDT");
} else {
	SerialUSB.println("Last reset was not caused by WDT");
}
```

* Explain how to set up registers / the different ways to
* Does not explain where the register names come from