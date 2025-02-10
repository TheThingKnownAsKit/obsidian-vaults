I have not taken any of the prerequisite classes and I am a freshman. I will write the notes assuming everyone going into the class will be similar to me, but I am aware that is not the case. Looking for feedback on feasibility of my notes
# GENERAL NOTES
* Grading rubrics in submission details would be nice (reach goal). Something like:

| POINTS -><br>CATEGORY             | 0-10                                                          | 10-20 | 20-30                                                                                                                                                      | 30-40             |
| --------------------------------- | ------------------------------------------------------------- | ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| Task 1 completion                 | The task was not completed or had very limited functionality. |       | The task is completely functional and well designed.                                                                                                       |                   |
| Task 2 completion                 |                                                               |       |                                                                                                                                                            |                   |
| Task 3 completion                 |                                                               |       |                                                                                                                                                            |                   |
| Task 4 completion                 |                                                               |       |                                                                                                                                                            | Task 4 exclusive? |
| Development documentation quality | Included very little or none of the required information      |       | Included the development plan, process, register configuration, troubleshooting, code snippets, acknowledgement of outside resources                       |                   |
| Testing quality                   | There was little to none sufficient testing                   |       | Each task was thoroughly tested with will documented results and troubleshooting steps                                                                     |                   |
| Report completion                 | The submission was missing most or all of the required items  |       | The assignment was submitted on time and included:<br>a PDF explaining each task and screenshots, if any<br>all the code created with proper documentation |                   |
Rough concept, not at all supposed to be accurate/comprehensive

* The report format is confusing and inconsistent with labs. Every lab had new report requirements, and sometimes it felt like some requirements were implied but left out of the instructions in some labs. I had no idea what it meant when I looked at it, and I could be missing common information from prerequisite classes. I would like to make the format more uniform and make it clearer what is wanted of the student.
	* *Would a whole PDF dedicated to submission details be worth it? It seems kind of complicated to me, and repeating it at the end of every lab would be tedious/very long*
		* How lab specific are the requirements? 
	* Note: It might just be me but I usually complete assignments first, then look at what I need to submit. In lab 1, I did not do any of the documentation before finishing the lab. Perhaps mention it earlier? Mostly student error but still beneficial to account for
		* *Put a section before the task assignment that tells the student to start their development process?*

* It is difficult to read the datasheet even when you've found the specific information you were looking for.
	* Maybe part of lab 1 could be a "How to Read the Datasheet" section? Like I didn't know what bits or registers really meant, so trying to figure out how to use datasheet information, which speaks exclusively in bit and register talk, was difficult and frustrating.
		* I have realized from the playlist that how to read the datasheet is briefly covered in the lectures. I still think teaching this in a hands-on way early into the class would be valuable, but it's less urgent. Telling a student what the datasheet tells them is a lot different than teaching them how to interpret it themselves. (Like showing the result of an equation and not the equation itself. How did we get here? What are the steps?)
		* Or part of the setup PDF?
		* Or it's own separate PDF?
		* Would an entire lab dedicated to datasheet comprehension help? Feels like the biggest barrier in the entire class (possibly due to my inexperience)
			* Foundation of the class, without high comprehension it'll be a struggle. One of my biggest challenges so far
			* Not just important to the class but working with embedded systems as a whole, could be worth the time
			* Could ty it into teaching the report format in the first two general notes. Whole lab dedicated to a. datasheet comprehension and b. how to go about assignments properly (setting up development plans, setting up testing) and recording it
	* The first lab deals a lot in getting students to explore the datasheet, which is good, but the datasheet is also over a thousand pages long of terminology students might not be familiar with. Especially since the lack of familiarity can make it difficult to even understand where to look. For example, while doing lab 1 and looking for the register to report the WDT reset cause, I thought it'd be under WDT but it was under Power Management. Some gentle direction/terminology translation would be nice

# UPDATES
I do not believe there is a way to color code command blocks

Horizontal lines and info boxes:

---
> [!Note]
> Test


# SETUP
Double check information in Arduino from command line is accurate
Also in the command line section, is there a different command for windows that would work instead of having to use a third party command line?

# LAB 2
Under the SAMD21 Timer Interrupts section I tried to explain what each interrupt actually is since the original PDF did not do that. I do not understand the last two and want to double check the first two are accurate