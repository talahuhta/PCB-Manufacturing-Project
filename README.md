# PCB-Manufacturing-Project
<img src="/pictures/Testing3.jpg" width="600">

## Overview
The primary goal of this project was to learn the practical process of creating a simple PCB from the design to the finished working device. It is based on the theory learned in the Introduction to Electronics course offered at the University of Oulu and manufactured at the university Fab Lab.

The device itself is a very simple circuit utilizing the oscillation function of the 555 timer IC to modulate the frequency of a piezoelectric buzzer by adjusting a potentiometer. The initial circuit diagram was provided by the course, however, everything else has been done from scratch including modifying the circuit to use the available Fab Lab components.


## Design
The design process began during the course after we had covered all the basic electronics theory and components. We were given a circuit diagram to follow and then were tasked with creating the PCB layout in the free software KiCad. All of the following was done in KiCad 9.0 aside from the software which runs the actual machines.

<img src="/pictures/Schematic.jpg" width="400">
<img src="/pictures/Design3.jpg" width="400">

Initially this was the end of the project and all that needed to be done for the course, however,  we decided to revisit the project and make it real. In terms of design this meant the components needed to be replaced with ones we had on hand which required a redesign of both the circuit diagram and PCB layout. This wasn’t too difficult as we had most of the same components aside from needing a new switch, potentiometer, and 4 pin connector. For this, we imported the Fab Lab component pack into KiCad and replaced all the prior components.

This also required getting the solder mask layer and creating a silk screen layer with a custom design which would be used later. Once all the layers had been made it was a matter of getting the gerber files for milling and PDFs for printing the solder mask and silk screen.

The components for the circuit:

<img src="/pictures/components.jpeg" width="400">


## Manufacturing Process

### Milling:

#### Setting the material

<img src="/pictures/adjuster.jpeg" width="400">

Mechanical milling was chosen over chemical etching due to Fab Lab availability and faster iteration time. For the milling process we needed to set up the copper plate in the mill. The mill has a vacuum feature that sucks the plate into the platform once it starts milling. The user just needs to tape the copper plate to stop additional movement. The material we had available was one-sided FR-4.

#### Working area setup

<img src="/pictures/Milling.jpg" width="400">

In the mill program we imported the files for the milling and drilling. The files for milling were in the format of .gbr or Gerber files. The drilling instructions are entered with the .drl files. After importing the files we had to set up the working area and the presets for the chosen material. 

The setup of the working area is done by utilizing the built in camera in the mill. There is no precise laser pointer attached for alignment of the machine. The tool of the machine can be moved with the mouse, so it was a quick process.

#### Tool calibration

We checked the usage hours of the milling bits and saw that the 0.2mm bit was way overdue (~200% of recommended usage) for a change so we switched it. The new bit had to be calibrated with the adjustment ring attached to the tool. The calibration process included milling a short line in the material and then seeing the result from the camera. In the camera display you could measure the width and adjust the tool accordingly. The limit for width that was given to us was being within +/-10% of the desired width. We adjusted until we got a 0.217 millimeter cut (0.2mm in the program).

The drill had a similar calibration process. The area tool milled away the area left inside the cuts for the wiring. The calibration process for that tool required inspecting a circle area cut to see that it completely milled away the area without any left over. This was done by only visual confirmation with bare eyes.

#### Milling and drilling

After the setup process we just had to keep watch over the machine. This was mainly to make sure that the correct switching of the tools was successful. After the machine finished, we cleaned up the residue with paper.

<img src="/pictures/MilledBoard.jpg" width="400">


### Printing:

<img src="/pictures/alcohol.jpeg" width="400">

Before printing a protective coating we cleaned up the pcb with isopropyl alcohol. After that we set up a piece of A4 in the UV inkjet printer we had. First we printed an edge cut rectangle where we could put the pcb. This was essentially a way to tell the machine where the pcb was. We added the silkscreen layer on top of the edge cut drawing so we could get the alignment right for the pcb.

<img src="/pictures/pdf.jpeg" width="400">

<img src="/pictures/printersoftware.jpeg" width="400">

Inside the software we told the printer to add a white layer under the black coating so that the resulting coating has the right coloring. The first time we printed without the silkscreen in the edge cut and our board was flipped so the coating failed. We learnt from our mistakes and the second time was successful.

<img src="/pictures/PrintedClose.jpg" width="400">


### Reflow Soldering:

Once the solder mask and silkscreen had been printed onto the board it was time to add solder paste, components, and use the reflow oven. We used a low temperature solder paste which was added to all the pads under a microscope:

<img src="/pictures/MicroscopeFar.jpg" width="400">

Then the components were added precisely with tweezers onto the solder paste, however, it would have been better to press the components down as it caused problems later on.

<img src="/pictures/InScope2.jpg" width="400">

With the board prepped for the reflow oven, we set the rails in the to the correct size and selected a temperature profile for which it began to preheat. After preheating to 150 C the board was placed inside and the program started. We were using the LF Small program which peaked the temperature at 240 C and then slowly brought down the temperature.

<img src="/pictures/OvenFar.jpg" width="400">

Unfortunately this temperature profile was too much for the coating and the solder mask boiled, and the components were not on perfectly needing touch up. It would have been better to use a lower temperature profile as we were using low temperature solder paste and it would have been better for the silkscreen and mask.

<img src="/pictures/OvenClose2.jpg" width="400">


#### Touch up:

Because the reflow soldering had not fully connected the components to the board it required some touch up. This involved hand soldering the components that were not fully connected and melting and adjusting the components that were stuck at a strange angle. This is also when the through hole components were soldered, which in this case was just the 4-pin-connector. Due to the PCB only being once sided the connector had to be added in a way in which the pins stuck out on the other side of the board, although this wasn’t a big issue.


### Testing:

For testing the circuit we input 5V DC power through it generated by a bench supply. At first we tried to get some sound out of the speaker circuit we had, but as it didn’t work we figured it had too much resistance. After that we inspected the pins leading to the buzzer component with a multimeter. We saw that it did produce an AC voltage of about 100mV. This indicated that the 555 timer IC we had was working correctly with the circuit. 

We then acquired a piezoelectric buzzer component and got it to work:

<video width="320" height="240" controls>
  <source src="/pictures/testing.mp4" type="video/mp4">
  s
</video>

The buzzer produced a pitch that seemed too high at some parts of the potentiometer’s range. This was due to us substituting a 33 nF capacitor with a 10 nF capacitor. We modified the circuit by resoldering a 100 nF capacitor in place of the 10 nF component. We found that this produced an audible pitch in all parts of the potentiometer’s range.

## Challenges

Throughout the process of the project we certainly had a few challenges, though in the end most of them were resolved. In the design phase we needed to accommodate and redesign for fab lab components and this took some time away from being able to actually make the board. In the milling process we ran into overdue drill bits that needed replacing, however this process generally went very well. In the printing process it was a learning curve of using the machine and properly aligning the material in the printer. One misprint had us buffing off the print from the contacts, but it came off just fine.

The biggest challenge came in the soldering process. Using the microscope to add solder paste to the pads worked, however it resulted in unreliable results and a mask to add it would work much better. Placing the components by hand also requires some practice as it is very precise and pushing the components down a bit would have yielded better results. Then the temperature profile which cause the mask to boil was major problem as it started to peel off. This made the retouch process more difficult as the solder began to bridge connections to ground. The hand soldering to retouch also worsened to the boiling of the mask and in the end it no longer held too well.


## Conclusion and Thanks

This project successfully demonstrated the full process of designing and manufacturing a simple PCB, from schematic creation to a functional finished device. It reinforced the electronics theory learned in the course while providing practical experience with PCB layout, milling, solder mask printing, and reflow soldering.

Although challenges were encountered, particularly during soldering and temperature profile selection, troubleshooting these issues proved to be an important part of the learning process. Overall, the project was a valuable hands-on experience and a strong foundation for more advanced PCB designs in the future. Thanks to the University of Oulu Fab Lab for providing the facilities and support for this project.
