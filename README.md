# Experiment-1
# Aim:
To do the DC analysis,Transient and AC analysis of a CS amplifier circuit and 
extract the various parameters associated using LT Spice.
# Components required: 
N Mosfet(nmos4),Resistor(22k),voltage supply(1.8V,0.9V) and connecting wires.
# Theory:
Mostfet is one of the most important compontent in electronics .
This importance is due to the fact of its compact design , low power consumption ,simple geometry and compatibilty in VLSI technology.
There are three different configurations in which the mosfet can be connected (namely common drain,gate and source) the most popular being common source and common drain configurations.
The Mosfet acts as an amplifier in the saturation region of operation where Vgs > Vth,Vgd < Vth and Vds>=Vov for an N channel mosfet.In the common source configuration there is a 180 degree phase shift 
between input and output. There is very high input impedance (Ig=0) ideally infinite.The drain curret **Id= .5*kn*Vov^2**;**Vov=Vgs-Vth & kn=W/L*u*Cox** for lambda = 0.
Output is taken from the drai end rather than simply across the resistor to maintain the common ground referance.
# Procedure:
**DC Analysis:** Set up the circuit as per the circuit diagram with proper connections ensuring valid circuit for further analysis.
Apply the DC voltage of Vdd=1.8V and Vgs = 0.9 V . Go to simulate option in the tab and edit simulation command, click on DC analysis and press ok.
Click on Run in the tab menu to get the DC operating point ,Vout and Id.

**Transient Analysis:** Apply a sine wave input of Vgs=0.9V with an amplitude of 50mV and frequency of 1kHz by going to advanced menu in the voltage setting option.go to simulate option in tab ,edit simulation command 
, click on transient analysis and give the stop time as 3m and click ok. Now Run to visualise the response of the circuit to a time varying signal.

**AC Analysis:** Go to spice directive and give the library file path for the simulator to access the data through the path . go to simulate option in the tab , edit simulation command , click on AC analysis 
and mention the time of sweep as decade , no of points as 20 and frequency as .1Hz to 1THzand click on ok.Now Run to analyze the gain and frequency response of the circuit.
# Circuit Daiagram:






	
