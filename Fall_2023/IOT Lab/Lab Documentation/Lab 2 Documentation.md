# Task Requirements
* Toggle two LEDs:
	* Turn on the yellow LED for 1 seconds, and turn it off for 1 seconds
	* Turn on the blue LED for 0.5 seconds, and turn it off for 0.5 seconds
	* Print out a message every time an LED changes its state:
		* "Yellow LED is on/off."
		* "Blue LED is on/off."
# Development Process
* Task 1:
	* Read instructions
	* Reference example
	* Implement example and alter it with information learned from the datasheet to support multitasking instead of just blinking one LED
	TABLE
* Task 2:
	* Read instructions
	* Reference example
	* This one is more difficult. Take a day or two to learn C++ basics, it's hard enough learning these things let alone not knowing what all the syntax means
	* Start with the given example. It needs to be heavily altered to support multitasking
	TABLE
* Task 3:
	* Read instructions
	* Reference work completed in Task 2 and alter it for one timer purposes
	* Requires significant reworking since it uses a generic clock generator 2 instead of a compare value. Look through the datasheet to figure out how to do this
	TABLE
# Test Plan
* All tasks:
	* Since all of these tasks are accomplishing the same thing with different methods, one testing strategy is mostly sufficient
	* Monitor the Serial Monitor output to observe the LED behavior. The Yellow LED should be toggling once a second, and the Blue LED every half second. The output to Serial Monitor should reflect this
	* Monitor the actual LED behavior itself. Keeping in mind that these will feature inaccuracies and will not be exactly on time. You the stopwatch feature of the Clock app on phone and take a lap every time the light toggles on/off
TABLE
# Results
* Task 1:
	* The Serial Monitor showed that the Blue LED was toggled twice was often as the Yellow LED. The actual lights are more difficult to interpret. They seem like they're both more or less blinking at the same periods, just on different cycles. I think this might be due to inaccuracies within the clocks themselves but I'm not sure. Might look into it later.
* Task 2:
	* Similar results as task 1. The Blue LED toggled twice as often as Yellow LED. The weird actual light timings were even more obvious here. I'm pretty sure I'm doing something wrong, they blink at the exact same periods just on slightly different cycles. They both toggled roughly every ~1.2 seconds