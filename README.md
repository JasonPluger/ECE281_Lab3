ECE281_Lab3
===========
###Explaination
####Moore Elevator Controller:
  To implement the moore elevator controller, I copied my MooreElevatorController_Shell.vhd file into my Nexys2_top_shell project and declared it as a component. I then created an instance of the MooreElevatorController within my top_shell and assigned the inputs to the 1.5Hz signal from the clockBus, reset to btn(3), and up_down and stop signals to switches on the board. I assigned my floor number output to nibble(0) so that it would display on seven-segment display #0. 
  
####Prime Number Elevator:
  To implement the prime number floors, I had to change 3 things: 1) The MooreElevatorController_Shell.vhd - added if statements to determine what to do at each of the different floors greater than 4. Also changed the floor output to an 8 bit std_logic_vector instead of 4 bit to accomodate double-digit numbers on the sseg display. 2) Changed the component and instantiation statements within Nexys2_top_Shell.vhd code to match changes within MooreElevatorController (8 bit instead of 4 bit). 3) Assigned sseg #0 the output of bits 7 downto 4 of floor, and sseg #1 the bits 3 downto 0 of floor.
  
####Switch-Controlled Elevator:
  To implement this switch-controlled elevator, I first changed my MooreElevatorController_Shell.vhd file by taking out the stop and up_down inputs and replacing them with a single input of 3 bit type STD_LOGIC_VECTOR. I modified by Nexys2_top_shell.vhd file to reflect this change. I then changed the Next-State Logic section of my MooreElevatorController_Shell.vhd file so instead of using an enumerated type for the floor_state signal, I changed it to a simple 3-bit STD_LOGIC_VECTOT as well. I then modified the Next-state logic to implement the new floors in 3 bit logic instead of the enumerated type. The output to the nibbles then had to be concatenated with an ampersand because they require a 4 bit input, instead of just a 3 bit one.
  
#### Critique:
#####Bad Code
```vhdl
nibble0 <= 
nibble1 <= 
nibble2 <= 
nibble3 <= 
```
These nibble-to-sseg instances are not assigned to anything. They must be assigned to _something_ prior to the code compilation. 
#####Good Code
```vhdl
nibble0 <= floor;
nibble1 <= "0000";
nibble2 <= "0000";
nibble3 <= "0000";
```
This code is better because each seven-segment display is at least getting some value assigned to it.

Functionality: Got my Moore Elevator Controller checked off by Dr. Neebel on 13 March 14 at 1428 - basic functionality.
               Got my prime number elevator checked on my Dr. Neebel on 13 March at 1530. 
               
               Sent a video of my switch-controlled elevator to Dr. Neebel and got it checked on 18 March 14

Documentation: Prelab: C3C ElSawaay explained his schematic to me, which made it click that each "component" statement in the Nexsys2 top shell module corresponds to a module inside the top shell. Pictorially, this is the same as having a box that does something inside a bigger box.
