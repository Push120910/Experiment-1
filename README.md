# Experiment-1
## Aim:
To do the DC analysis,Transient and AC analysis of a CS amplifier circuit and 
extract the various parameters associated using LT Spice.
## Components required: 
N Mosfet(nmos4,pmos4 ),Resistor(22k),voltage supply(1.8V,0.9V) and connecting wires.
## Theory:
Mostfet is one of the most important compontent in electronics .

This importance is due to the fact of its compact design , low power consumption ,simple geometry and compatibilty in VLSI technology.
There are three different configurations in which the mosfet can be connected (namely common drain,gate and source) the most popular being common source and common drain configurations.

The Mosfet acts as an amplifier in the saturation region of operation where Vgs > Vth,Vgd < Vth and Vds>=Vov for an N channel mosfet.
In the common source configuration there is a 180 degree phase shift between input and output. \
_There is very high input impedance (Ig=0) ideally infinite._

The drain current

**I<sub>d</sub> = 1/2*k<sub>n*(Vov)<sup>2</sup>**; **V<sub>ov</sub> = V<sub>gs</sub>-V<sub>th</sub>** **&** ****k<sub>n</sub>=W/L*u<sub>n</sub>*C<sub>ox</sub>**** for lambda = 0.

Output is taken from the drain end rather than simply across the resistor to maintain the common ground referance.
The different analysis i.e DC Analysis is done to ensure the mosfet operates in saturation so that the the mosfet works as an amplifier.

Transient Analysis is done to anlalise the response of the amplifier to the time varying input sine wave and the corresponding output.
AC Analysis is done to evaluate the gain of the amplifier which is **-gm*Rd**; _gm_ is transconductance of the amplifier.

## Procedure:
1.Create a new folder and name it as project file.Save the LT spice file in this folder.

2.Name the mosfet as CMOSN and the length as 180nm and width as 3um initially.

3.For the pmos name it as CMOSP and set the length as 180nm and width as 3um respectively

4.**DC Analysis:** Set up the circuit as per the circuit diagram with proper connections ensuring valid circuit for further analysis.
Apply the DC voltage of Vdd=1.8V and Vgs = 0.9 V . Go to simulate option in the tab and edit simulation command, click on DC analysis and press ok.(.op)
Click on Run in the tab menu to get the DC operating point ,Vout and Id.

5.**Transient Analysis:** Apply a sine wave input of Vgs=0.9V with an amplitude of 50mV and frequency of 1kHz by going to advanced menu in the voltage setting option.go to simulate option in tab ,edit simulation command 
, click on transient analysis and give the stop time as 3m and click ok.(.tran 3m) Now Run to visualise the response of the circuit to a time varying signal.

6.**AC Analysis:** Go to spice directive and give the library file path for the simulator to access the data through the path . Go to simulate option in the tab , edit simulation command , click on AC analysis 
and mention the time of sweep as decade , no of points as 20 and frequency as .1Hz to 1THzand click on ok.Now Run to analyze the gain and frequency response of the circuit.(.ac dec 20 .1 1T)
# Circuit 1:
![Image](https://github.com/user-attachments/assets/91f5eeff-ac7d-46ad-a605-490589fa519b)
# Calculation :
Power = 100uW

Loop Equation: V<sub>dd</sub>=V<sub>ds</sub>+I<sub>d</sub>*R<sub>d</sub>

P=I*V (I<sub>d</sub>=55.55 uA , V<sub>dd</sub>=1.8V)

clearly V<sub>ds</sub>=V<sub>out</sub>; V<sub>ds</sub>>=V<sub>gs</sub>-V<sub>th</sub>

R<sub>d</sub> (upon calculation) =22.6Kohm 

Widhth=0.3um(Vary width to get the current)

V<sub>ds</sub>=0.543

gain=-20dB(from AC analysis)

Q point is (0.543,55.55uA)
## Tabular Column :

|Width |  Current(Id) |  Vout |

|1um   |  74.2uA      | 0.122 |

|0.8um |  72.7uA      | 0.155 |

|0.7um |  71.65uA     | 0.18  |

|0.5um |  67.2uA      | 0.27  |

|0.3um |  55.55uA     | 0.543 | 
## Results:
1.**DC Analysis:**
![{A06C9B78-C43B-4E20-8A5D-057E6E112F4E}](https://github.com/user-attachments/assets/b3f1d952-b309-4d3e-89d1-c8f07572b7a8)
Id=55.55uA\
Vout=0.543V\
Width=0.3um\
DC Operating point : (0.543,55uA) is obtained for 0.3um Width and 180nm Length.

2.**Transient Analysis:**
![{605EA2A8-AD87-4D28-9DC3-1A41957672C0}](https://github.com/user-attachments/assets/caa420ce-e815-421f-a1f0-85d6357b24c3)
Vout=0.543V\
There is 180 degree phase shift between input and output or the DC level shift.

3.**AC Analysis:**
![image](https://github.com/user-attachments/assets/6781c492-a8bb-4e7a-9dba-b45579f2770a)
Gain=-20dB
## Circuit 2 :
## Inference:
1. Current is directly Propotional to the Width of the Mosfet and the current varies with the change in width.

2. Mosfet saturation ensures the mosfet works as an amplifier and produces the desired negative gain as per the equation Av=-gm*Rd.

3. Q point stability is attained in saturation region thus helping in attaining linear amplification .

4. The Mosfet gain is increased in mid band frequency range |(small signal analysis).












	
