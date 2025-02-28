## INTRODUCTION & LAST WEEK RECAP
Last week, we implemented an M2M-type network with our IoT nodes. In this lab, we will evolve our systems to make it an IoT system. The first three labs have already helped you to understand the basics of embedded systems to help you develop the Things, but IoT is not just about embedded systems. It's all about connectivity. The goal of this lab is to walk through that whole process and get a "Hello World!" message from a remote device into a gateway and onto the internet. First, we will create the gateway, then fire up a device to send the data, and finally create an internet application to look for the data.

**Takeaways from last week:**
* Modular design of the system for easy upgrade of system components.
* Wireless connectivity with radio.

## IoT OVERVIEW
* End Device/Node/Mote - an object with an embedded low-power communication device.
	* More reading: https://www.thethingsnetwork.org/docs/devices/
* Gateway - antennas that receive broadcasts from End Devices and send data back to End Devices.
	* More reading: https://www.thethingsnetwork.org/docs/gateways/
* Network Server - servers that route messages from End Devices to the right application and back.
	* More reading: https://www.thethingsnetwork.org/docs/network/
* Application - A piece of software running on a server.
* Uplink Message - a message from a Device to an Application.
* Downlink Message - a message from an Application to a Device.

### IoT vs M2M
IoT Systems may incorporate some M2M nodes (such as a Bluetooth mesh using non-IP communication) but aggregate data at an edge router or gateway. An edge appliance like a gateway or router serves as the entry point onto the internet. Alternatively, some sensors with more substantial computing power can push the internet networking layers onto the sensor itself. Regardless of where the internet *on-ramp* exists, the fact that it has a method of tying into the internet fabric defines IoT.

By moving data onto the internet for sensors, edge processors, and smart devices, the legacy world of cloud services can be applied to the simplest of devices. Before cloud technology and mobile communication became mainstream and cost-effective, simple sensors and embedded computing devices in the field had no reasonable means of communicating data globally in seconds, storing information for perpetuity, and analyzing data to find trends and patterns. As cloud technologies advanced, wireless communication systems became pervasive, new energy devices like lithium-ion became cost-effective, and machine learning models evolved to produce actionable value. This significantly improved the IoT value proposition.

### LoRaWAN Overview
LoRaWAN is a media access control (MAC) protocol for wide-area networks. It allows low-powered devices to communicate with Internet-connected applications over longrange wireless connections. LoRaWAN can be mapped to the second and third layers of the OSI model. It is implemented on top of LoRa or FSK modulation in industrial, scientific, and medical (ISM) radio bands. The LoRaWAN protocols are defined by the [LoRa Alliance](https://www.lora-alliance.org/) and formalized in the LoRaWAN Specification, which can be [downloaded](https://www.lora-alliance.org/lorawan-for-developers) on the LoRa Alliance website.

IoT is the idea that we can add interconnectivity to many things we interact with daily. For example, if your refrigerator kept track of what was inside and could talk to your cell phone, you wouldn't be left wondering if you needed to buy milk at the store. Your phone would be able to tell you how much milk the fridge had left. So, the Internet of Things is about connectivity.

Connectivity is well-solved in the home with WiFi and Bluetooth, but what if your refrigerator was in the middle of a field without access to the internet? This is where LoRa comes in. ***LoRa*** is "Long Range" radio designed for low power consumption and long-range transmissions at the expense of bandwidth. This means you can send a little bit of data a long way. Then you need something dedicated to bridge from LoRa messages to internet traffic - called a "gateway." If you have something that can speak both LoRa and "Internet," then you could make your solution, but there is a more accessible and better option. This is where LoRaWAN comes in.

***LoRaWAN*** is a public specification for the system that would be at Starbucks listening for messages from the fridge. A critical benefit of LoRaWAN is that you can send encrypted data during transmission, and your fridge could get up and walk to the next state over (again - just a metaphor!). The messages could still be picked up by a gateway someone else had built. Since the messages are secure, that person won't know about your stinky cheese, but the message will still get back to you over the internet. Groups like [The Things Network](https://thethingsnetwork.org/), [Azure IoT Hub](https://azure.microsoft.com/cloud_platform/iot_solutions/), [AWS IoT](https://aws.amazon.com/iot/) organize everyone's efforts to make this possible.
![[architecture.png]]

## HARDWARE
### The Things In Your Hand
* Your End Device - SparkFun Pro RF: This is the remote system sending data. We will set up a device to send the "Hello World!" message in the section "Turning a Gateway into a Device".

* Your Gateway - **SparkFun ESP32 Things 1-Channel Gateway**: This is the name of the ESP LoRa Gateway 1-Channel acts as the bridge that speaks both WiFi and LoRa. The "Single-Channel LoRa Gateway" section will cover all the steps needed to make this happen.

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

### SparkFun LoRa Gateway - 1-Channel (ESP32)
![[15006-SparkFun_LoRa_Gateway_-_1-Channel__ESP32_-01 1.jpg]]

* ESP32-WROOM-32 module
	* WiFi, BT+BLE microcontroller
	* Integrated PCB antenna
* Hope RFM95W LoRa modem
	* Frequency range: 868/915 MHz
	* Spread factor: 6-12
	* SPI control interface
* U.FL antenna connector for LoRa radio
* Reset and ESP32 pin0 buttons
* 14 GPIO ESP32 pin-breakouts
* Power and user LEDs

## SETTING UP 1-CHANNEL GATEWAY
### Installing ESP32 Arduino Core
The ESP32's relationship with Arduino is growing, and now it is straightforward to install the core - the Arduino IDE can handle it nearly independently.

1. Implement the ESP32 board dependency.
	1. Ensure you have Arduino IDE version 1.8 or later installed.
	2. Navigate to `File -> Preferences`.
	3. Open the additional board manager URLs menu.
	![[OpenAdditionalBoardsvView.png]]
	4. Then paste the following link below the SparkFun board manager URL:
		```
		https://dl.espressif.com/dl/package_esp32_index.json
		```
		
		![[ESP32AdditionalBoardPaste.png]]
	1. Accept the changes and restart the Arduino IDE.

---

2. Install the SparkFun ESP32 board.
	1. Navigate to `Tools -> Board -> Boards Manager` or select the second icon on the vertical left list. Then, install the latest version of `SparkFun ESP32 Boards` by SparkFun Electronics.
	![[InstallSparkFunESP32Board.png]]

It might take a while to install. Once it has successfully been installed, restart the IDE for good measure.

<br>

### Upload Blink
To make sure everything is ready, let's blink the LED. Ensure the correct board is selected:
* `Tools -> Board -> SparkFun ESP32 Boards -> SparkFun LoRa Gateway 1-Channel
* `Tools -> Port -> [Correct Port Selected]` - The correct port will vary by person.
* `Tools -> Upload Speed -> 115200`

Then, to test that thing's are working properly:
* Open the "Blink" example (`File -> Examples -> 01.Basics -> Blink`).
* Upload the code.
* After the code has been compiled and transferred to the board, the pin 17 LED should begin blinking.

Now that you control the ESP32, we can move on to exciting things! The remaining portions of this guide will focus on sending a "Hello world!" message from a LoRa device to the internet.
<br>
NOTE: If you are experiencing a path compilation error, proceed to the Python3 Fix section. This is an error that MacOS and some Linux users will experience.

## HELLO WORLD USING LoRa
### Python3 Fix (Required for MacOS and Linux Users)
Since Apple upgraded MacOS Monterey to 12.3, Arduino is not able to find python. Apparently, there is no more python 2.7 in MacOS. Our SparkFun package uses an outdated version of esp32 libraries that are looking for python 2.7. The same problem may occur on Linux as well. This is the error you could get when you try to compile the simple Blink code:
```
exec: "python": executable file not found in $PATH
Compilation error: exec: "python": executable file not found in $PATH
```
<br> 

To fix this error:
1. Check that python is installed.
	1. Open a Terminal and type `python -V`. The version will vary but as long as a version of Python 3 is installed it should work.
	2. You can also find its path by running the command `where python3`. You will need this path later so save it somewhere.

---

2.  Locate the problem path and update with the python3 path.
	1. Open the Arduino IDE and navigate to `File -> Preferences`.
	2. Find the line `Show verbose output during` and check both `compile` AND `upload` boxes. This will provide more information during compile.
	![[ShowVerboseOutputDuring.png]]
	3. Compile the code again and check the last line before the errors. It should produce something like this:
		```
		python [$HOME]/Library/Arduino15/packages/SparkFun/hardware/esp32/1.0.0/tools/gen_esp32part.py
		-q
		[$HOME]/Library/Arduino15/packages/SparkFun/hardware/esp32/1.0.0/tools/partitions/default
		...
		```
	4. Now, you know the path to your SparkFun folder. Then, in the terminal go to the following folder:
		```
		$HOME/Library/Arduino15/packages/SparkFun/hardware/esp32/1.0.0/
		```
	5. Edit the `platform.txt` file with an editor such as vi.
		1. Change the following line:
			```
			tools.gen_esp32part.cmd=python "{runtime.platform.path}/tools/gen_esp32part.py"
			```
		2. Into (Make sure you add the 3 at the end of python):
			```
			tools.gen_esp32part.cmd=/usr/bin/python3 "
			{runtime.platform.path}/tools/gen_esp32part.py"
			```

---

3. Update the `esptool` binary file.
	1. Look through the error from 2.3 again. You should find something related to a binary called `esptool` that is located somewhere like:
		```
		$HOME/Library/Arduino15/packages/esp32/tools/esptool_py/2.6.1
		```
	2. Because we use an outdated esp library, we need to update this. Here is a quick (yet messy) hack to do this. Navigate to `File -> Preferences` and open the Additional Board Manager URLs editor. Paste the following url into the editor:
		```
		https://espressif.github.io/arduino-esp32/package_esp32_index.json
		```
	3. Then, navigate to `Tools -> Board -> Board Manager` and search for esp. Install `esp32 by Espressif Systems`. This will create a new folder 4.5.1 under the esptool_py folder above.
	![[InstallESPOldVersion.png]]
	4. Now, we will copy the new `esptool` into the 2.6.1 folder. Run the following commands in the terminal:
		```
		cp $HOME/Library/Arduino15/packages/esp32/tools/esptool_py/4.5.1/esptool
		$HOME/Library/Arduino15/packages/esp32/tools/esptool_py/2.6.1
		```

Now, it should compile and the pin 17 LED should blink.

Credit: 
https://forum.arduino.cc/t/esp32-problem-with-compilation-on-macos-12-3-monterey/969771
https://forum.arduino.cc/t/mac-os-update-killed-esp32-sketch/969580/7

### Setting up the Single-Channel LoRaWAN Gateway

**DO NOT PRESS THE RESET BUTTON ON YOUR GATEWAY BOARD DURING THIS SECTION!**

#### Making a LoRa Gateway
Thanks to 915 MHz LoRa AND WiFi connectivity, the LoRa Gateway 1-Channel is a useful gateway in a LoRaWAN network. This section will show you how to make your own gateway and access it on the internet. You should already be able to program the LoRa Gateway 1-Channel. The next step is to download a library to run LoRaWAN and modify it to suit our board and needs.

1. Download and install the libraries.
	1. Download the modified ESP 1-ch Gateway code from Canvas (`ESP-1ch-Gateway-v5.0-Azure.zip`) and unzip it.
		1. The hookup guide by SparkFun still uses v5 and not the current version, so this lab will use the modified version based on the archived v5 copy.
		2. If you would like to learn more, you can access: [GitHub by things4u](https://github.com/things4u/ESP-1ch-Gateway-v5.0), [Original Archived V5](https://cdn.sparkfun.com/assets/learn_tutorials/8/2/6/ESP-1ch-Gateway-v5.0-master.zip) (Use the modified archived version on Canvas).
		<br>
	1. This zip file contains both Arduino sketches and libraries, so before compiling the sketch you will need to extract the libraries. Navigate to `ESP-1ch-Gateway-v5.0-Azure/libraries` subfolder and copy all its contents into `Documents/Arduino/libraries/` (all common in OSX, Windows, and Linux).
		1. **Do NOT update the libraries.** The IDE might prompt you the next time you open it to update these libraries. DO NOT UPDATE THEM. If you do, delete the updated libraries and copy/paste from the zip file again.
		2. Note: do NOT copy the libraries folder directly as this may delete the existing Arduino libraries.
		Your libraries folder should look something like this when you're done, but the exact details will depend on your operating system and where you store your Arduino files.
		![[ESP32InFileSystem 1.png]]
---

2. Configure the Gateway Sketch.
	1. ESO-sc-gway.h configuration:
		1. Go to the `ESP-sc-gway/` folder and open the `ESP-sc-gway.ino` with the Arduino IDE. This will open multiple tabs including all .ino and .h files in the folder. Before uploading the `ESP-1ch-Gateway` sketch to your board, you will need to modify a few files.
			1. Note: Use Ctrl-F to search the file for the setting you want to modify.
			2. There are a lot of values that can be optionally configured that are not required by this course. If you would like to look into it more, read the [editing the ESP-sc-gway.h](https://github.com/things4u/ESP-1ch-Gateway-v5.0#editing-the-esp-sc-gwayh-file) part of the GitHub README.
			<br>
		2. Radio Settings:
			1. [REQUIRED] `_LFREQ` - set to 915 (US, will vary by country)
				1. This sets the frequency range your radio will communicate on. This is not the group's frequency.
			2. `_SPREADING` - you can use SF7, SF8, SF9, SF10, SF11, or SF12.
				1. Affects what devices your gateway can communicate with.
			3. `_CAD` - set to 1.
				1. this is the Channel Activity Detection. If enabled (set to 1), CAD will allow the gateway to monitor messages sent at any spread factor. The tradeoff is that the radio may not pick up very weak signals.
				<br>
		3. Hardware Settings:
			1. `OLED` - the SparkFun board does not have an OLED, so set to 0.
			2. `_PIN_OUT` - set to 6.
				1. This configures the SPI and other hardware settings. We'll add a custom hardware definition later.
			3. `CFG_sx1276_radio` - ensure this is defined and `CFG_sx1272_radio` is NOT
				1. This configures the LoRa radio connected to the ESP32.
				<br>
		4. The Things Network (TTN) Settings:
			1. There are parameters related to the TTN in the code because this code was originally developed for TTN. However, TTN no longer supports our gateway. So the sketches are updated for Azure. Keep the TTN related code as they won't be used but commenting them out or deleting them may cause issues.
			<br>
		5. WiFi Settings:
			1. [REQUIRED] Add at least one WiFi network to the `wpas wpa[]` array. **Leave the first entry blank**. You will need to enter a password into the password section, which you will do in a later section.
				1. For example, `wpas wpa[] = { { "", "" }, { "NU-IoT", "<YOUR GATEWAY NU-IOT PASSWORD>" } };`
				2. You can also add other WiFi networks by creating additional entries. Make sure you add a coma at the end of the Nu-IoT lime before creating a new entry on a new lime below it.
				<br>
	2. loreamodem.h configuration:
		1. This file defines how the LoRa modem is configured, including which frequency channels it can use and which pins the ESP32 uses to communicate with it. Be careful modifying most of the definitions here.
		2. Locate `int freqs[]` under `#elif _LFREQ==915` and modify the frequencies with the frequencies assigned to your group. The current code is defined based on a center frequency of 915. If your assigned frequency is 906 MHz, then modify 914xxxxxx , 915xxxxxx , 916xxxxxx to 905xxxxxx, 906xxxxxx, 907xxxxxx, respectively. More specifically:
			1. Essentially, your group's assigned frequency is your center frequency. The channels you are given must be defined in a range, so they should always follow the format of 9[n - 1]900000, 9[n]900000, 9[n + 1]600000 where n is the last two digits of your assigned frequency. If n is a single digit number, pad with one 0.
			2. Another example is if you're assigned frequency is 912, then n = 12. Therefore, your three replacement numbers are 911900000, 912900000, and 913600000.
			```
			914900000 -> 905900000,
			915100000 -> 906900000,
			...
			916600000 -> 907600000,
			```
			<br>
	1. ESP-sc-gway.ino configuration: 
		1. Open the file and locate the following line:
			```
			static const char* connectionString = "<YOUR AZURE CONNECTION STRING>";
			```
		1. We will update this variable after enabling our Azure IoT hub device in the Azure portal. For now, leave it unchanged.

---

3. Upload the Code and Check NU-IoT WiFi Connection.

After configuring the gateway project, upload it to the board. The code is not yet ready to connect to Azure but we will first if we can get connected to the NU-IoT WiFi network. Without the Wi-Fi network, our device will not have a link to connect to the Internet. UNL Wi-Fi is now open for IoT device enrollment, through the NU-IoT network.

Your gateway is already registered for the NU-IoT network and your group can receive a password by:
1. The passwords for each SparkFun Gateway is unique for each one, and in order to find the password for your device we will need the serial id.
2. Open the serial monitor.
3. Follow the instructions just below this to attempt to compile the code. This will take a very long time and will end in an error. However, by compiling the code you can find the serial id.
4. Once compilation is finished, a message should be printed to the serial monitor that resembles the picture below. The code highlighted is the serial id. Show the serial id to a TA and they will find the corresponding password for you
	![[FindingSerialID.png]]

Now, make sure you modified the password field in the `ESP-sc-gway.h`. Try compiling and uploading the sketch to your ESP32 with the program. This time it should properly compile, though it will fail to upload to IoT Hub since we are setting that up in the next section. Make sure the following are selected:
* Tools->Board->SparkFun ESP32 Boards->SparkFun LoRa Gateway 1-Channel
* Tools->Port->[Correct Port Selected]
* Tools->Upload Speed->115200

After it's uploaded, open up your serial monitor and set the baud rate to 115200. The sketch may take a long time to set up the first time through -- it will format your SPIFFS file system and create a non-volatile configuration file. Once complete, you should see the ESP32 attempt to connect to your WiFi network, then initialize the radio.
Among the serial monitor message you should see the following:
```
...
Connection successful
...
Initializing the IoT hub failed..
```

The first message shows that you are where you want to be, connected to Internet. The second message tells you we still have work to do to connect to Azure.

<br>
<br>
<br>

## SETTING UP THE AZURE IoT HUB
Now, we are going to update codes for gateway-to-cloud communication. By default, the things4u implementation works for the things network. However, the network has stopped supporting all single-channel gateway devices. Therefore, we will use Microsoft Azure IoT hub instead of the things network for the cloud service. We need to make a few changes in the source code for that.

### Create a Student Account
Go to [Azure for students](https://azure.microsoft.com/en-us/free/students/) and click start free. Log in with your UNL email and password. Then, activate your student benefit credit in that account.

### IoT Hub
Navigate to the homepage of Azure. Click 'Create a resource' in the Azure portal. In the search box, search "IoT Hub" and select it. Then click create.

![[AzureHome.png]]

![[CreateIOTHub.png]]

Under the basics tab:
* Select 'Azure for Students' as the subscription.
* Add it to a resource group. If you do not have a resource group then create a new one, the name does not matter.
* Put a name for your IoT hub, the name does not matter.
* Select the region as 'Central US'.
* Select the 'Free Tier'. This will set your message limit at 8,000 per day. Keep this in mind when programming your device.
	![[HubCreationMenu.png]]

Click 'Review + create'.
Review your settings and ensure they are correctly configured. Select 'Create'.

### IoT Device for the Hub
Next, it's time to add a device to the newly created hub. Open your new hub, click 'Add and configure IoT Devices' in the middle of the screen under the Next steps tab.

Click 'Add Device'.
* Assign it a Device ID.
* Select Authentication type as 'Symmetric key'.
* Check the 'Auto-generate keys' option to enable it.
* Enable 'Connect this device to an IoT hub'.
Click 'Save' to finish creating the device.

Now, click on that device. This will show the information about the device. Copy the **Primary Connection String** of it. This connection string needs to be added to `static const char* connectionString` variable inside the `ESP-src-gway.ino` code from the Making a LoRa Gateway section. Do this now before moving on.

### Test Gateway - Cloud Connection
Compile and upload your updated gateway code. You should see the following in the serial monitor. If the initialization is still failing, ensure you have followed the setup steps properly to up until this point.
```
...
Info: >>>Connection status: connected
Initializing IoT hub success.
```

## SETTING UP YOUR END-DEVICE
Now, we will connect one of the SparkFun Pro RF boards to the Gateway and eventually to the cloud. We will start by installing the LMIC library.

### Installing LMIC Library
* Why not Radiohead?
	* Radiohead is an capable but limited library for accessing the radio chip hardware. It is not designed for LoRaWAN standardized work.
* What is LMIC (LoraMAC-in-C)?
	* LoRa MAC implementation in C
	* A real-time OS supports it
	* LoRa communications are supported
	* Highly professional and integrated library

We'll set up the SAMD21 Pro RF as a node using a library written by Matthijs Kooijman, a modified version of the "IBM's LMIC (LoraMAC-in-C)" library. The latest repo is maintained by a company named MCCI.

You can download and manually install it from the [GitHub Repository](https://github.com/mcci-catena/arduino-lmic/archive/refs/heads/master.zip). Once you download the zip file go to `Arduino IDE->Sketch->Include Library->Add .ZIP Library` and select the zip file. You'll see a Library installed message.

### Configuring LMIC Library
Now that LMIC is installed, it's time to configure it.

**The LoRa settings should match**. The spreading factor, frequency, and bandwidth should match your gateway configuration.
1. This modified example takes directly from the example code provided by the library with two changes: the function calls to "Serial" will need to be replaced with "SerialUSB" and changes to the pin mapping that is consistent with the SAMD21 Pro RF. Before we look at the code, you'll need to modify the `lmic_project_config.h` file that came with the LMIC Arduino Library.
2. [**Sanity Check**]
	1. Find your Arduino libraries folder and navigate to `...libraries/arduino-LMIC/project_config/` or `...libraries/MCCI_LoRaWAN_LMIC_library/project_config/`
	2. Locate the file called `lmic_project_config.h` and open it in any text editor.
	3. Find the lines where `CFG_us915` is defined. It should look like this:
		```
		// project-specific definitions
		//#define CFG_eu868 1
		#define CFG_us915 1
		//#define CFG_au915 1
		//#define CFG_as923 1
		// #define LMIC_COUNTRY_CODE LMIC_COUNTRY_CODE_JP      /* for as923-JP; also define CFG_as923 */
		//#define CFG_kr920 1
		//#define CFG_in866 1
		#define CFG_sx1276_radio 1
		//#define LMIC_USE_INTERRUPTS
		```

In `Lab04_LMICClient.ino`, **modify LMIC.freq to the assigned team frequency**. Ensure this is one of the frequencies that you have used in the `loramodem.h` assignment of frequencies.
	E.g., an assigned frequency of 915Mhz would be 914900000 in both `loramodem.h` and `Lab04-LMICClient.ino`

Now, there are some edits to the sketch code itself to incorporate these new functions.
* Change your serial library lines of your SAMD21 Pro RF to `SerialUSB`.
* Comment out the line `while(!SerialUSB)`. Instead, in `setup()` add a `delay(1000);`
	* Waiting for a serial connection is not the best approach in case you'd like to power your end device with any other means.
	* Additionally, if your gateway and node are connected to the same computer, in most cases, you cannot monitor both serial ports through Arduino.

Try compiling and uploading the sketch to your SAMD21 Pro RF with these changes. Make sure the following are selected:
* `Tools -> Board -> SparkFun SAMD Boards -> SparkFun SAMD21 Pro RF`
* `Tools -> Port -> [CorrectPort]` - The correct port will vary by computer.

## RECEIVING DATA ON AZURE FROM YOUR DEVICE
### Stream Your Data
Now, we have both devices ready and cable to transmit and receive LoRa packets. In addition, in Azure, we have an IoT device inside the Azure IoT hub. To access data from this device, we need a "Stream Analytics job" or any other equivalent data access resource. In this lab, we will utilize the Stream Analytics job.

Navigate to the Azure homepage and click the 'Create a resource' button and search for the Stream Analytics job.
![[CreateStreamAnalyticsJob.png]]

After clicking the create button, we have to fill in the required information:
* For subscription, use 'Azure for Students'.
* Use the same resource group as the IoT Hub.
* Name the stream.
* Select 'Central US' as the region.
* Select 'Cloud' as the hosting environment.
* Set the 'Streaming units' to 1.
	![[CreateStreamMenu.png]]

Navigate to the newly created deployment (select 'Go to resource' button).
![[StreamOverview 1.png]]

Next, we need to configure the inputs for this job.
* First, click on 'Inputs' in the left sidebar.
* Click 'Add input' from the top bar and select 'IoT Hub' from the drop-down menu.
	* Give an alias name and choose your IoT Hub from the drop-down menu. The rest of the configuration settings should auto complete.
	* Click 'Save'. Now, your IoT Hub is connected as an input stream.
	![[AddInput.png]]

For this lab, we won't need any output source. Instead, we'll query the input stream directly to see the data sent to IoTHub. For this, click 'Query' on the left (shown in the last two images).
* It should automatically select the input you just created. If it did not, ensure you correctly created an input.
* Copy and paste the following code into the query:
```
SELECT
	*
FROM
	[INPUT_ALIAS] // Replace with your input alias. Make sure to keep the brackets
```

Check your results in the following section.
### Testing the Stream
**NOTE!** Before connecting the end-device and gateway, make sure to **connect their antennas**, so that they can communicate.

Once everything is connected, you should see the results listed below for all three of the sections.

The SparkFun Pro:
![[TestQuerySparkFunProOutput.png]]

The SparkFun LoRa Gateway:
![[GatewayTestQueryOutput.png]]

The Test Results section of the Query:
![[TestResultsQueryTest.png]]

## ASSIGNMENT
In this lab, you will work with your teammates and improve our IoT system. A lab report is required from each group, one per group. You will need to work together as you need to share the gateway. Each member must provide the individual screenshots of their Azure account and serial monitor outputs in the group report. Make sure you have Azure account results **from each team member** in your report.

### Requirements
1. Finish the helloworld example **for each team member**.
	1. Record the procedure of setting up the link from your device to the IoT Hub with screenshots.
2. Use the code from the previous lab (Lab 3) and merge it with the LMIC example code for packet transmissions.
	1. Remove the radio operations in the Lab 3 code and instead, use the LMIC code.
	2. Use your packet construction modules, average temperature reading modules, etc. from Lab 3.
3. Maintain your packet structure from Lab 3 and make necessary changes in the gateway to prepare a JSON data packet. Then, send packets with temperature sensor data to the Azure cloud every 60 seconds. Instead of using timers, use LMIC's TX_INTERVAL.
4. Download the JSON file from Azure and share the contents of it in the report.

### Results
1. Code that fulfills each requirement in this lab.
	1. Each function in this system should be separately presented with an explanation. The entire code snippet will not be accepted.
2. Serial message from.
	1. Sparkfun pro RF device
	2. LoRa gateway
3. Screenshots from Azure and JSON for the data reporting results.

### Report
* Record your development process.
* **Acknowledge any resources that you found and helped you with your development (open-source projects/forum threads/books)**.
* Record the software/hardware bugs/pitfalls you had and your troubleshooting procedure.
* Results
	* Required results from the section above.
* Appendix
	* The entire program (Arduino sketch) in the Appendix (No screenshots will be accepted). Include only those sketches that you modified.

### Submission Instructions
1. Submit your lab on Canvas on or before the deadline.
2. Your submission should include one single PDF explaining everything that was asked in the tasks and screenshots, if any.
3. Your submission should also include all the code that you have worked on with proper documentation (Do not attach your code separately as an .ino file. Instead, copy and paste your code in the Appendix. Do not use screenshots in the Appendix.).
4. Failing to follow the instructions will make you lose points.

## REFERENCES
1. [SparkFun LoRa Gateway 1-Channel Hookup Guide](https://learn.sparkfun.com/tutorials/sparkfun-lora-gateway-1-channel-hookupguide/all)
2. [LoRaWAN with ProRF and The Things Network: Example IFTTT Integration](https://learn.sparkfun.com/tutorials/lorawan-with-prorf-and-the-thingsnetwork/all#example-ifttt-integration)
3. [Internet Of Things Shows](https://www.youtube.com/playlist?list=PLlrxD0HtieHh5_pOv-6xsMxS3URD6XD52)
4. [SparkFun SAMD21 Pro RF Hookup Guide](https://learn.sparkfun.com/tutorials/sparkfun-samd21-pro-rf-hookupguide/lorawan-arduino-library-and-example)
5. Lea, Perry. Internet of Things for Architects: Architecting IoT solutions by implementing sensors, communication infrastructure, edge computing, analytics, and security. Packt Publishing Ltd, 2018.