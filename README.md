ECE281_Lab3
===========
###Analysis
Moore Elevator Controller:
  To implement the moore elevator controller, I copied my MooreElevatorController_Shell.vhd file into my Nexys2_top_shell project and declared it as a component. I then created an instance of the MooreElevatorController within my top_shell and assigned the inputs to the 1.5Hz signal from the clockBus, reset to btn(3), and up_down and stop signals to switches on the board. I assigned my floor number output to nibble(0) so that it would display on seven-segment display #0. 

Functionality: Got my Moore Elevator Controller checked off by Dr. Neebel on 13 March 14 at 1428 - basic functionality.

Documentation: Prelab: C3C ElSawaay explained his schematic to me, which made it click that each "component" statement in the Nexsys2 top shell module corresponds to a module inside the top shell. Pictorially, this is the same as having a box that does something inside a bigger box.
