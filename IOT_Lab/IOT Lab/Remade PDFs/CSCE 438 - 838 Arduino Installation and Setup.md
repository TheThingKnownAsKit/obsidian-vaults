## GETTING STARTED
### Hardware Requirements
1. Computer (Windows 10/11, Linux(ubuntu), MacOS)
2. Arduino board (SparkFun Pro RF) - Provided by lab
3. USB Micro B cable - Provided by lab

### Software Requirements
You have multiple options for the programming environment of Arduino. The Arduino IDE is the official software and it is the easiest and most simple one. Advanced options such as VSCode and Atmel studio 7 are also very good but still require that the Arduino IDE be installed to use the drivers and libraries. If you are more comfortable with these IDEs, you can also use them.
* Arduino IDE (*Recommended*)
* VSCode
* Atmel Studio 7

### Introductory Information
* What is Arduino?
	* https://www.arduino.cc/en/Guide/Introduction
* Guide to Programming Arduino.
	* https://www.arduino.cc/en/Guide/Environment

### Datasheets
You will frequently reference datasheets throughout this course. It is recommended to save these somewhere you will easily be able to find them.
* Sparkfun Pro RF graphical datasheet: https://cdn.sparkfun.com/assets/e/0/6/6/5/SamProRF_Graphical_Datasheet_Updated.pdf
* SAMD21G datasheet: https://cdn.sparkfun.com/assets/6/3/d/d/2/Atmel-42181-SAM-D21_Datasheet.pdf
<br>
<br><br><br><br><br>
### Hardware Handling Guide
![[EditedSparkfun.png]]

<span style="color:blue">BLUE RECTANGLE:</span>
USB Micro B cable input.

<span style="color:green">GREEN CIRCLE:</span>
Manual reset button.
To reset, double tap the small black button on the side then hold it down for 5 seconds. It should start slowly flashing blue if properly reset.

<span style="color:orange">ORANGE HEXAGON:</span>
Antenna connection.

<span style="color:red">RED DOTS:</span>
Anything easily breakable.

## SETUP PROCEDURE
### 1. Download and Install The Arduino IDE
You will need to download and install the Arduino IDE even if you choose to use another IDE.

Select the link to go to the Arduino website: https://www.arduino.cc/en/Main/Software
The link will bring you to the following webpage. Select the appropriate download option from the highlighted red box.

![[ArduinoDownload.png]]

After the installer finishes downloading, open the file and configure the download to your preferences.

### 2. Install Drivers
#### Windows 10/11:
1. Plug the USB Micro B cable into the board and your computer.
2. Windows should automatically search the Internet for the drivers. You should not have to do anything.
#### Mac and Linux:
1. You should not need to download anything. The device should show up as a serial port as soon as it's plugged into your computer.

### 3. Setting Up Arduino IDE
1. Install Arduino SAMDS Board.
	1.  Open the Boards Manager.
		1. Second vertical icon to the left of the screen and under the file icon.
		2. OR, alternatively, select Tools from the menus in the top right and navigate to `Tools -> Board -> Boards Manager`.
	2.  Search SAMD.
	3. Install the latest version of `Arduino SAMD Boards (32-bits ARM Cortex-M0+)`.
	![[SAMDDependency.png]]

---

2. Install SparkFun SAMD Board.
	1. Scroll down from the SAMD search or search SparkFun SAMD.
	2. Install the latest version of `SparkFun SAMD Boards`. The dependency version must be greater than or equal to the SAMD Boards version.
	![[SparkfunDependency.png]]

---

3. Install SparkFun Board Definition.
	1. Open your Arduino preferences (`File -> Preferences`).
	2. Find the Additional Board Manager URLs text box and paste the following link in the field encapsulated by the red box.
		```
		https://raw.githubusercontent.com/sparkfun/Arduino_Boards/master/IDE_Board_Manager/package_sparkfun_index.json
		```
	![[BoardManagerURL.png]]

At this point, the IDE should be able to identify your SparkFun board. If it cannot, revisit the previous steps to ensure you did everything correctly.
### Procedure for Uploading Your Program
1. Select programmer.
	1. Navigate to `Tools -> Programmer` and select `Atmel-ICE` for the SAMD21 board.
	![[SelectProgrammer.png]]

---

2. Select board.
	1. Navigate to `Tools -> Board` and select `SparkFun SAMD21 Pro RF`.
		If the wrong board is selected, you may not be able to compile your sketch due to the wrong definitions. Even if it passes compilation, it may fail to upload.
	![[SelectBoard.png]]
---
3. Select port.
	1. Now you need to check your port. Navigate to `Tools -> Port`. The IDE may somehow magically know which port the SAMD21 board is in. Otherwise, you will need to select it yourself.
		1. On Windows, the serial port should come in the form of `COM#`.
		2. On Mac or Linux, the port will look like `/dev/cu.usbmodem####`.

---

4. Select port baud rate.
	1. Navigate to `Tools -> Serial Monitor`. A new window at the bottom of the screen should pop up.
	2. The baud rate should be automatically configured but you should double check. You will also need this number for programming use.
	![[BaudRate.png]]

You need to do the four above steps EVERY time you upload code. You will likely not need to reselect some of these, but it's good practice to check all of these things to ensure everything is working properly.

In summary:
1. Select programmer: `Atmel-ICE`
2. Select Board: `SparkFun SAMD21 Pro RF`
3. Select port: `COM#` or `/dev/cu.usbmodem####`
4. Select port baud rate: should be 9600

### Command Line Integration (REQUIRED for Linux)
NOTE: This step is REQUIRED for Linux users in order for the Arduino IDE to work. If you do not use Linux, this is an optional step.
<br>
Arduino has a command-line application that is capable of performing all Arduino tasks from the command line without using any GUI. This application is known as arduino-cli. If you want to use the command line instead of the GUI or are a Linux user, this will show you how to set it up. Otherwise, skip this.

1. To install the latest version of arduino-cli, use the follow command in the terminal:
```
curl -fsSL https://raw.githubusercontent.com/arduino/arduino-cli/master/install.sh | sh
```
NOTE: sh is not a recognized command on the Windows command line. You can use third party command lines, such as GitBash, to execute the command.

---

2. Next, initialize the config file at the home directory using the following command:
```
arduino-cli config init
```

![[Pasted image 20240123154928.png]]

---

3. Paste the board manager URL in `additional_urls:`
```
https://raw.githubusercontent.com/sparkfun/Arduino_Boards/master/IDE_Board_Manager/package_sparkfun_index.json
```

---

4. Now, arduino-cli can collect necessary packages to run SparkFun devices with the following commands:
```
arduino-cli core update-index
arduino-cli core install arduino:samd
arduino-cli core install SparkFun:samd
```
<br>
You're done! You can now use the Arduino IDE directly from the command line. Here are some useful commands:

**Creating a New Sketch**
```
arduino-cli sketch new SketchName
```

**Compile and Upload Code to Sparkfun**
```
arduino-cli compile --fqbn SparkFun:samd:samd21_proRF SketchName
sudo arduino-cli upload -p /dev/ttyACM0 --fqbn SparkFun:samd:samd21_proRF SketchName
```

**Find Out the Serial Port for the Connected Device**
```
arduino-cli board list
```
![[Pasted image 20240123155741.png]]

## WRITING YOUR FIRST SKETCH
Congratulations! Installation and setup is complete. It's time to write a test sketch to ensure everything is working properly.

### "Hello World" With Embedded Systems: Print
In this sketch, you will be using serial communication to let your board send a message containing "Hello, world!" to your computer and print it to the serial monitor. Remember to open the serial monitor to view the message.

If you need a new sketch to write in, navigate to `File -> New Sketch`.
Copy the following code into the sketch.
```C++
void setup() {
	SerialUSB.begin(9600);
	SerialUSB.println("Hello, world!");
}

void loop() {
}
```
Follow the steps to upload your code and see how it runs.

Additionally, you can add a line to make the program wait until the serial monitor is open to print the message. Otherwise, since the program only prints it once, you can miss it if you didn't already have the serial monitor open.
	Optionally, add this before the print statement: `while(!SerialUSB);`

### "Hello World" With Embedded Systems: Blinking LED
In this sketch, instead of printing "Hello, world!" to the serial monitor, you will be blinking an LED on and off with the GPIO ports on the board. It can be helpful to consult the SparkFun Pro datasheet to determine which LED is which.

Copy the below code into your sketch.
```C++
// LED definitions in the datasheet
// D13 (PIN_LED_13): Blue
// TX (PIN_LED_TX): Green
// RX (PIN_LED_RXL): Yellow

void setup() {
	Serial.begin(9600);
	// Setup the pin as OUTPUT
	pinMode(PIN_LED_13, OUTPUT);
}

// Blink LED with 1 second delay.
void loop() {
	// HIGH is on, LOW is off
	digitalWrite(PIN_LED_13, HIGH);
	// Freezes the program for a specified time in miliseconds
	delay(1000);
	digitalWrite(PIN_LED_13, LOW);
	delay(1000);
	// The sketch will loop from here continuously
}
```
The blue LED should alternative on/off every one second. 