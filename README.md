ECE281_Lab3
===========
###Analysis
Moore Elevator Controller:
  To implement the moore elevator controller, I copied my MooreElevatorController_Shell.vhd file into my Nexys2_top_shell project and declared it as a component. I then created an instance of the MooreElevatorController within my top_shell and assigned the inputs to the 1.5Hz signal from the clockBus, reset to btn(3), and up_down and stop signals to switches on the board. I assigned my floor number output to nibble(0) so that it would display on seven-segment display #0. 
  
Prime Number Elevator:
  To implement the prime number floors, I had to change 3 things: 1) The MooreElevatorController_Shell.vhd - added if statements to determine what to do at each of the different floors greater than 4. Also changed the floor output to an 8 bit std_logic_vector instead of 4 bit to accomodate double-digit numbers on the sseg display. 2) Changed the component and instantiation statements within Nexys2_top_Shell.vhd code to match changes within MooreElevatorController (8 bit instead of 4 bit). 3) Assigned sseg #0 the output of bits 7 downto 4 of floor, and sseg #1 the bits 3 downto 0 of floor.

Functionality: Got my Moore Elevator Controller checked off by Dr. Neebel on 13 March 14 at 1428 - basic functionality.
               Got my prime number elevator checked on my Dr. Neebel on 13 March at 1530. 

Documentation: Prelab: C3C ElSawaay explained his schematic to me, which made it click that each "component" statement in the Nexsys2 top shell module corresponds to a module inside the top shell. Pictorially, this is the same as having a box that does something inside a bigger box.
