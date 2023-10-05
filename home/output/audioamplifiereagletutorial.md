---
title: Audio Amplifier Eagle Tutorial
description: 
published: true
date: 2023-10-05T18:29:15.843Z
tags: 
editor: markdown
dateCreated: 2023-09-22T00:22:01.945Z
---

# Audio Amplifier Eagle Tutorial
***Part 1:***
*****Check out your first PCB Layout*****
Eagle allows us to do two main things: Create schematics, and use those schematics to create printed circuit board (PCB) layouts. The layouts are the digital version of the circuit boards, such as the green ones inside your laptop. For now, we will just look at the layout. 

1. Head BACK to TinkerCAD and go to the circuit you created with the three resistors. Hopefully, you took our advice and relabeled your circuits as you go; otherwise, you should notice things start getting messy!
2. In the top right, click the "Send to" button.
3. In the pop-up, click the ".BRD" button under the "Electrical Design Files" heading. 
4. The file will download to your computer, probably in your "Downloads" Folder inside your user directory. The file extension should be .brd for the file. 
5. Head back to Eagle now. In the Control Panel, there is a left-hand menu. Click Projects >> projects:
![image_1_eagle.png](/image_1_eagle.png)
6. Copy or move the .brd file downloaded in Step 4 into the projects folder shown above (the easiest way is to drag it from your Downloads folder and drop it onto the projects folder). 
7. In the Eagle Control Panel, double-click the board file. You should see a new window appear with the title starting as "1 - Board - ...".

***Part 2:***
In Part 1, you learned how to export layouts from TinkerCAD to Eagle. For this homework, we will learn how to edit the layout. 
1. Head BACK to TinkerCAD and go to the circuit you created with the three resistors in 4.4. 
2. Recall from “Check out your first PCB Layout” section in Part 1. Export an Eagle “.BRD” file from the TinkerCAD and open it in Eagle software.  **Make sure you save this PCB layout, we will use it for Part 3 next week.**
3. Learn about the software user interface: 
![image_2_eagle_ttt.png](/image_2_eagle_ttt.png)
- Icons on the left side of the software are some common ***functions*** such as delete, move, mirror. 
- You may also type “delete”, “move” in the ***Command line*** to use these functions.
- Pay attention to the ***status bar*** at the bottom; it gives you hints about how to perform certain actions. For example, when I choose the Move function, the status bar will show: “Left-click to select the object to move”. Hit “Esc” to exit the current function.
- ***Airwire*** shows potential connections between components. They need to be replaced by copper wires to make real electrical connections in the software. 
- The golden wire around the components (rectangular shape) are ***board outline***. It indicates the dimension of your board.
- This symbol ![image_3_eagle.png](/image_3_eagle.png) represents the ***origin***, or (0, 0), of the board. I suggest putting the bottom left corner of the board on this point.
- Eagle uses a unit called “***mil***” to represent distance. A mil is 1/1000 of an inch, or 1000 mil is 1 inch. You can see your mouse’s current location coordinates in the top left corner, in mils: ![image_4_eagle.png](/image_4_eagle.png) ![image_5_eagle.png](/image_5_eagle.png)
- Click the “move” function ![image_6_eagle.png](/image_6_eagle.png)or type “move” in the command line. Find the resistor you want to move, and ***left click*** on the “+” on the resistor symbol to pick up the component. After picking up the component, you may ***Right click*** to rotate the component or drag your mouse to move the components. ***Left click*** to confirm the change.  Move all the components to the left corner. Below is an example of a 2 resistor circuit; ***you should have 3 resistors***. 
- Use the same move function to shrink the yellow board outline as shown below. (I am using 2 resistors as an example here; ***you should have 3 resistors***) 
![image_7_eagle.png](/image_7_eagle.png)
***Part 3***
In Part 1, you learned how to export Schematics from TinkerCAD to Eagle. In Part 2, you learned how to edit and modify the PCB layout. For this homework, we will learn how to connect components with copper traces in the layout software. 
<!---
1. placeholder to fix number Markdown issue
1. -->
1. Open your A02 Eagle Layout in Eagle.
2.  Load up a Design Rules Check (***DRC***) file. This file makes sure you’re following a set of rules about how far apart components are from each other, among other things. We will provide you with a  tad265 DRC file that is configured correctly for our PCB fabrication machine (PCB mill).   Download the tad265 DRC file: tad265 DRC. (Very very important!) and save the file to: "***Documents\EAGLE\design*** rules" in the Eagle Control Panel.
-  Click “DRC” on the left bottom corner. (or go to “Tools-> DRC”):
![image_8_eagle.png](/image_8_eagle.png)
-  Click Load…and choose the ***tad265_drc.dru*** file you just downloaded. Click ***Apply***.
-  Make sure the left corner of DRC window should show ***“DRC(tad265_drc)”***
![image_9_eagle.png](/image_9_eagle.png)
-  Close the DRC window!
7.  Connect components with ***copper wires***. Select “Route”  or go to “Edit-> Route”. Click and follow the yellow airwires to connect components (I am using 2 resistors as an example here; ***you should have 3 resistors***). 
![image_10_eagle.png](/image_10_eagle.png) 
8. DRC check. Open the DRC window again. Click “Check”. Make sure there is no error popped up. In the ***status bar***, you should see “DR4C: No errors.”
<!---
1. placeholder for proper number formatting 
1. -->
***Part 4***

In Part 1, you learned how to export Schematics from TinkerCAD to Eagle. In Part 2, you learned how to edit and modify the PCB layout. In Part 3, you learned how to connect components with copper traces manually in layout software. For this homework, we will learn how to perform an Autoroute.
1. Head back to TinkerCAD and go to the parallel circuit you created for circuit 4.
2. Download EAGLE **.BDR** file and open it in EAGLE software. 
3. Load up the **tad265.drc** file you downloaded in A03. <span style="color:red">**(Very, very important!)**<span>
4. Move and rotate components to make the board smaller. Adjust the board outline just like you did in Part 2.
5. connect components with ***copper wires***. Select “AutoRoute”![image_11_eagle.png](/image_11_eagle.png). In the setup window, make sure to select “N/A” for Top and “Auto” for Bottom. Click “Continue…”. A new window will appear, hit “***Start***”.
![image_12_eagle.png](/image_12_eagle.png)
6. A new window will appear, hit “Start”. The software will automatically connect all the traces for you. Once the analysis is complete, choose any routing variant that is marked “100%” complete. You ***must click “End Job”*** to close the window, otherwise, you won’t be able to run other autoroutes.
![image_13_eagle.png](/image_13_eagle.png)
7. DRC check. Open DRC again, click “Check”. Make sure there are no errors popping up. In the **status bar**, you should see “DRC: No errors.”

***Part 5***
<!---
1. placeholder for proper number formatting 
1. -->
In the past assignments, we learned how to download a schematic from TinkerCAD and export to EAGLE. If we would like to edit the Schematic, we would have to change the design in TinkerCAD, download a new .brd file and start over. In this assignment, we would like to show you how to create a schematic in Eagle software which can be converted into a .brd file. These two documents will be synchronized, i.e. whatever you changed in schematic will automatically apply to the PCB layout.  

Here is my demonstration [video](https://youtu.be/qm8M5Q1QJYA) and a [tutorial](https://learn.sparkfun.com/tutorials/using-eagle-schematic) from Sparkfun which will help explain any of the steps below:

1. Eagle typically opens up to the Control Panel. Under the “**Projects**” tab are two folders: **projects** and **examples**. The **projects** folder is where you’ll create all new projects. Start by creating a new **project** named “A05” by right clicking the projects folder and selecting “New Project”. 
2. Make sure the **green circle** is next to your project. This means that project is the Active project. When we have multiple files, as this little green indicator links them all together. 
3. In the project, create a new schematic:
![image_14_eagle.png](/image_14_eagle.png)
4. This automatically opens the schematic editor, where you can create a new schematic.
5. Save your schematic. Give it a filename **a05_combination_username.sch**, where username is replaced with your username.
6. Create the following schematic (see below the schematic for some hints that’ll help you find parts and use the software):
![image_15_eagle.png](/image_15_eagle.png)
- Parts are found under the Add button:      									![image_15_1_eagle.png](/image_15_1_eagle.png)
- Parts are organized in libraries and sub-libraries based on their type or manufacturer. Until you’ve used Eagle a lot, finding parts is kind of a pain. This table should help find every part in the above schematic:
![image_16_eagle.png](/image_16_eagle.png)
- Wires are called “Nets” in Eagle, and are green in the schematic (not to be confused with lines, which do not provide connectivity in the diagram; it’ll matter later). There are two ways to use nets; Press the Nets button (![image_17_eagle.png](/image_17_eagle.png)), or simply type “nets” and hit enter.

- Nets need to connect to parts. It’s easy to create a net that appears to connect to a part, but doesn’t. Anytime you’re creating nets, make sure you see the green circle, which means you are connecting the net to the part.
![image_18_eagle.png](/image_18_eagle.png)
- Nets also need to connect to other nets. Nets sometimes need to cross paths, but not connect. Be sure you can identify the difference:
![image_19_eagle.png](/image_19_eagle.png)
- Eagle works in “Modes”. For example, if you’re in creating nets mode, you can’t move parts. To exit a mode, hit **ESC** on your keyboard, then select the next mode. By default, you’re in “Move” mode, which lets you select and move parts and nets. Other modes include rotate, mirror, delete, and many more.
- Once you have completed your schematic, run an "**ERC**” (Electrical Rule Checking) check to see if you have bad connections. Click “Tools -> ERC” to make sure you have **0 Errors**. 
7. From your finished schematic, click the “Switch to board” button  in the taskbar. It will ask you to create a new .brd file. Click yes.  It will open the PCB layout window. Make sure <span style="color:red">**DO NOT**</span> close the schematic window. Save the .brd file (Click File >> Save). You should see a new file called a05_combination_username.brd file automatically generated in the project file. 
![image_20_eagle.png](/image_20_eagle.png)

**The schematic window and PCB layout window will be synchronized, if you close one, you will lose the synchronization.** In the PCB layout windows, all components are packed on the left bottom corner with several yellow wires linked. These yellow wires are not actual wires, they are the “airwires” to show the connection based on your Schematic wiring. If you change the schematic wiring, the yellow connection will change. 

Important Rules!

There is a **link** between your board and your schematic, so if you change one, it’ll change them both. This is extremely important, because otherwise changes you make to your schematic **won’t** be reflected on the physical board, and your layout will be useless. 

These two files are linked automatically, but it is easy to accidentally break that link. Here’s how to ensure you don’t do that:
- **Rule #1**: In the Control Panel, make sure the green dot is lit next to your project by clicking it:
![image_21_eagle.png](/image_21_eagle.png)
- If you don’t have a green dot at all, you didn’t create a project first. Make sure you create a project, then create a schematic inside the project. 

- **Rule #2**: When you close one file (.sch or .brd), close them both. Don’t edit with one file closed! Eagle will warn you like this:
![image_22_eagle.png](/image_22_eagle.png)
-	If you get this warning, open up both files and it should go away. DON’T make edits when this warning is displayed!

- **Rule #3**: Keep the file names the same, except for the extension:
		![image_23_eagle.png](/image_23_eagle.png)
	If you change one, change them both. They are linked by their filename, and changing one will break the link. 
- **Rule #4**: Always switch back and forth between the schematic and board using the  quick button. This ensures you are looking at the linked files (and not some other spurious file you may have created). 

**Part 6**
<!---
1. placeholder for proper number formatting 
1. -->
Recall from Assignment Part 5, to draw a schematic in Eagle, you need to first create a “**New Project**” named “**Part 6**”. You may also review my demonstration video here. In the project, create a new schematic named “**a06_AudioAmplifier_username.sch**” where the username is replaced with your username. 

Create the schematic for the Audio Amplifier as shown in Figure 1 below. Here is the video from [Part 5](https://youtu.be/qm8M5Q1QJYA) and [tutorial](https://learn.sparkfun.com/tutorials/using-eagle-schematic) from Sparkfun. 

![image_24_eagle.png](/image_24_eagle.png)
Schematic for the Audio Amplifier

The table below will help you find every part in the Schematic. 

![image_25_eagle.png](/image_25_eagle.png)


Once you find all the components, use “rotate” and “move” to properly locate your components. Use the “**net**” tool to wire them together. Once you complete the schematic wiring, we need to assign values to these parts. 
You can assign values through the  “Parts” windows. 

![image_26_eagle.png](/image_26_eagle.png)
1. Double click on **R1** and the software will highlight the R1 resistor in the schematic. The “**Properties**” window will pop up. 
2. Put **470** in the “**value**” section. Hit “OK”. 
3. Assign values to R1-R3, C1, C2 and the variable resistors based on the schematic above. You can also change the designation name through the “properties” window. For example, I changed the name for AB9V to “9V”. You don’t have to change it, it’s up to you. Pick names that it’s easy for you and your teammates to understand. 
4. Right click on the **Ground** node (Wires that connected to **GND**), select properties **make sure the Net name is GND**
5. **You may choose “ERC” to see if you have bad connections. Click “Tools -> ERC” to make sure you have 0 Errors. **
 ![image_26_eagle.png](/image_26_eagle.png)
### Eagle Layout
From your finished schematic, click the “Switch to board” button  in the taskbar to create the PCB layout. We discussed the synchronization between Schematic and Layout in A05. Before we go too far, let’s talk about some important rules so you don’t waste your time. 

==Important Rules!==
There is a link between your board and your schematic, so if you change one, it’ll change them both. This is extremely important, because otherwise changes you make to your schematic won’t be reflected on the physical board, and your layout will be useless. 

These two files are linked automatically, but it is easy to accidentally break that link. Here’s how to ensure you don’t do that:
In the Control Panel, make sure the green dot is lit next to your project by clicking it:
		
If you don’t have a green dot at all, you didn’t create a project first. Make sure you create a project, then create a schematic inside the project. 
When you close one file (.sch or .brd), close them both. Don’t edit with one file closed! Eagle will warn you like this:
	
If you get this warning, open up both files and it should go away. DON’T make edits when this warning is displayed!
Keep the file names the same, except for the extension:
		
If you change one, change them both. They are linked by their filename, and changing one will break the link.
Always switch back and forth between the schematic and board using the quick button: . This ensures you are looking at the linked files (and not some other spurious file you may have created). 
How to use Eagle Layout Editor
In the past assignments, we have learned several Eagle layout functions including rotation, adjust the size, apply DRC, manual route and auto route. In this assignment, you will use what you have learned so far to complete the Audio amplifier layout. You will also learn how to apply copper pour and how to export files for production. 
Step 0: Save your .brd and .sch file, and save them often	
Step 1: Loading up tad265 DRC file
Recall A03 step 2. 
Step 2: Resize of your board. 
Recall from A02
Your board should have a maximum dimensions of 1400mil x 1900mil. 
Step 3: Move your components into the board outline
Before moving the components into the board outline, think about how your board will look, for example, you may want to put a battery clip and Speaker at the edge of your board. 
Refer to the schematic and move the components one by one into the board space.  (inside the white dimension box). For example, resistor R1 and LED D1 will be in series, so naturally, we would like to put them next to each other. Capacitor C2 is connected to Pin 7 of LM386, therefore, placing C2 next to Pin 7 is probably a good idea. Untangle the airwire as much as possible. 
Step 4: Route the PCB board (Manual route or Auto route)
Method 1 - Autoroute: Recall A04 
Method 2- manual route:  Recall from A03. To create routes, use the route icon  . Once you click the icon you’ll have new options in the taskbar at the top. Make sure these are set to the following before creating routes:

Change “1 Top” to “16 Bottom”.
Change width to 20.

	

**Tips: **
Unlike the schematic, as you route you’ll want to avoid crossing wires. Because these traces will be copper lines. Unlike jumper wires that have a rubber outside, copper is a pure conductor. So those crossed paths result in shorts between the two nets/nodes. As we know, shorts are bad. Very bad!
Similarly, the green pads represent where components will be connected to the board, known as pads. These pads are electrically conductive too, so you don’t want to have a route going over a pad, unless it’s meant to connect there. Each pad typically has a drill hole in the middle, where your component will be mounted.
Most of the time, the software is smart enough that won’t let you route with a cross wire or going through a pad. However, when you move a wired component, the trace will be moved and could cross a pad or another trace. DRC check will help you figure that out. 

In both of the cases above, you also want to leave clearance between pads, routes, and the board edge. This is because the circuit mill is not perfectly accurate, and may sometimes cut too close to a pad or route, creating an open circuit. As we know, openings are bad. Not as bad as shorts, but still bad.
Step 5: Copper pour
You’ll also want to add a copper pour, which reduces the amount of cutting the mill has to do, as well as creates a large, grounded area on the board to reduce the possible noise in the system. To do this:
Go back to Layout, and select the polygon tool: 
On the menu, switch “1 Top” to “16 Bottom” since everything is on the bottom layer of our board.
Change the “Isolation” value to 20 (meaning there’ll be 20 mils between the copper pour and any traces that are not connected to it)
Then, draw a polygon around the entire board.
When the polygon is closed, a “Signal Name:” dialog opens. Put GND in the text box.
Lastly, hit the ratsnest button. You should see a large blue section appear on the board. 
To get rid of the copper pour (which will make viewing your other traces easier), in the command bar, type in ripup GND;  and hit enter. 
Step 7: DRC final check
Once you have your board 100% routed, we’ll want to run a design rules check (DRC) again. A DRC checks your circuit board for issues that may occur when cutting the PCB with the mill. Use the DRC file (same one as before) to find places where your circuit has issues.
If there are no issues, you’ll see a message at the bottom status bar saying “DRC: No errors.” Congratulations, you’re done!
If there are issues, a window will open. Click each issue, and it will show you where in the board you need to fix. Fix the issues by “ripping up” routes () and rerouting. You may also need to move around components, rotate them, etc. 
Sometimes it’s useful to ripup all routes to start over completely (yes, you’ll likely be doing this at least once). After you press the ripup button above, click the green light in the toolbar:  Alternatively, you can enter ripup * in the command prompt to do the same thing.
Exporting your Board from Eagle
Do these steps after your layout is completed, 100% routed, and passes the DRC with no errors.

First, download the following file:
Tad-265.cam - Performs three CAM jobs:
Generates the drill holes file (Excellon)
Generates the traces and pads file (Gerber)
Generates the dimension of the board (Gerber)
In Eagle, open the layout of your board (.brd).
Under File, open the Cam Processor.
Open up the CAM job downloaded above:
	
In the left hand section titled “Output files”, click each of the files for a06 (e.g., a06_username_drills, etc). Replace username in each of those files with your username.
In the bottom left, hit “Select Board”. Select your amplifier board.
Hit Process job. 

File exports are now complete. You should see three new files in your project: 2 Gerber (gbr) files, and 1 Excellon (xln) file. Take note of where those are located. You can close Eagle now. These files you generated will be imported in the PhCNC software later, which operates the mill. 

In this Google Drive folder, create a new folder with your username, and copy your 2 gerber files (dim and copper) and 1 Excellon file (xln) into your folder. Finally, copy our schematic (sch) and board (brd) files from Eagle. 