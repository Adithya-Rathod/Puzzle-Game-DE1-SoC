# About DE1-SoC
The DE1-SoC computer system has components which are implemented using both the FPGA and the HPS inside Intel's 
Cyclone V SoC chip. The FPGA implements two NIOS II processors and several peripheral ports. 
The HPS comprises an ARM Cortex A9 dual-core processor and a set of peripheral devices.

We will be giving inputs from the Host Computer through the JTAG ports to do the required
functions throughout the game and display the output onto a VGA display having pixel buffer which
provides an image resolution of 320 x 240 pixels.
# Overview of the Game
The Ring Puzzle game is a single person game designed entirely for DE1-SoC board in C language. This game requires the DE1-SoC board and external VGA display.

The motive of this game is to _rotate_ the three gears _clockwise_ and place all the RED dots over the triangle at the centre. The keys assigned for the rotation of the gears are:

G -> left gear

H -> right gear

B-> bottom gear

*This is the desired pattern by the rotation of the

gears.

### A glimpse...?
![A particular game completion instance](https://github.com/Adithya-Rathod/Puzzle-Game-DE1-SoC/assets/97827613/abeeab41-5377-410d-93ad-bd06dd515101)


## Demonstration
First the home screen loads and Welcomes is the user with two options either to start the game by pressing ENTER or read the rules using the TAB key.

***Home Screen:***

![The home Screen](https://github.com/Adithya-Rathod/Puzzle-Game-DE1-SoC/assets/97827613/f3f3bc36-9abd-46d4-aecd-2f5f1c9fb54f)

***The Rules page:***

![image](https://github.com/Adithya-Rathod/Puzzle-Game-DE1-SoC/assets/97827613/97573894-5a3d-41e2-8d24-c60757b7d372)

***The Puzzle Screen:***

![image](https://github.com/Adithya-Rathod/Puzzle-Game-DE1-SoC/assets/97827613/a52cd73a-0bb8-47ce-836d-1827aa178c2a)
*A randomized order of 6 RED and 6 GREEN dots is generated every time you start solving the puzzle*

 

 - **Press the G key on the host keyboard to rotate left gear, H for right and B for bottom (all clockwise).**
 - **After the puzzle is solved, a blinking effect mark the success of the game and user is prompted to go to the home screen which again
   restarts the game from home screen upon hitting the ENTER key.**

## Little logic please..!?

 - An array of 12 elements called alldots[12] is initialized with six 0s and six 1s. 
 - The randomize() function randomizes the array.
 -  This array is the randomized and fillMyArray() is called to fill the dots in the skeletal with appropriate colour (1 -> RED and 0 -> GREEN).
 - alldots[i] = 1 indicate that the $i^{th}$ dot is of the color **RED** and 0 indicates **GREEN** where $0≤i≤11$.
 - The entire structure is divided into 4 layers top, top mid (in code as tmid), lower mid (in code as lmid) and bottom.
 - Numbering is as follows: 
	 -  top is $i = 0, 1, 2$ 
	 - tmid is $i=3, 4, 5, 6$
	 - lmid is $i=7,8,9$
	 - bottom is $i=10,11$
		*all numberings are from left to right in the image*
6. The rotation logic is goverened by an auxilary array of same size as the main array but this time it will store the bit value on basis of the rotation of the requested ring(left right or bottom). Three Seperate functions concering theire roation are coded.  
8. Setting the while infinite loop and set the key bindings over the host PC to rotate the gears.
