##                               Experiment 1: PMOS Common Source Amplifier Design

## 1. Aim
    
  To design, analyze, and simulate a Common Source (CS) Amplifier using a PMOS transistor in 180nm technology.
  The primary goals are to fix the Quiescent point (Q-point), measure maximum signal swing, and evaluate bandwidth
  with and without capacitive loading—all while maintaining a power budget of $\leq 1\text{mW}$.

## 2. Components & Tools
   
1. __Software__: LTspice XVII / LTspice 24.

2. __Technology Node__: TSMC 180nm (tsmc018.lib).

3. __Active Device__: PMOS (CMOSP).

4. __Passive Components__: Resistor ($R_d = 4500\Omega$), Capacitor ($C_L = 10\text{pF}$).

5. __Voltage Sources__: $V_{DD} = 1.8\text{V}$, $V_{in}$ (SINE wave).

## 3. __Theory__ :

The Common Source (CS) amplifier is a fundamental stage in analog integrated circuit design used to achieve voltage gain.

__A. PMOS Operation__ :

Unlike NMOS, a PMOS transistor uses holes as charge carriers.
It is turned on by applying a Gate-to-Source voltage ($V_{GS}$) that is more negative
than the threshold voltage ($V_{th}$).
In this configuration, the Source is tied to the highest potential ($V_{DD}$).
   
__B. Region of Operation (Saturation) :__

  To achieve stable amplification, the transistor must be biased in the Saturation Region.
   
  In this region, the drain current ($I_D$) is relatively independent of the drain-to-source voltage ($V_{DS}$).
   
  Condition: $|V_{DS}| \geq |V_{GS} - V_{th}|$.
   
  Current Equation: $I_D = \frac{1}{2} \mu_p C_{ox} \frac{W}{L} (V_{SG} - |V_t|)^2$.

__C. Gain and Phase Inversion :__

  The small-signal voltage gain ($A_v$) is defined as the ratio of output voltage change to input voltage change.

  Formula: $A_v \approx -g_m R_d$, where $g_m$ is the transconductance.

  The negative sign represents a 180° phase inversion.
   As $V_{in}$ increases, the $V_{SG}$ decreases, lowering $I_D$.
  This reduction in current through $R_d$ causes $V_{out}$ to rise toward $V_{DD}$.

__D. Bandwidth and Capacitive Loading__

  Bandwidth is the frequency range where the amplifier maintains its gain.

  Without a load capacitor, the bandwidth is limited only by the internal parasitic capacitances of the MOSFET.

  Adding an external load capacitor ($C_L$) creates a dominant pole, which significantly reduces the high-frequency
      response.

## 4. Circuit Diagram:

  __Without capacitor :__

  ![Circuit without Cap](https://github.com/user-attachments/assets/2f655e11-fe43-4447-bfc1-e6a9bb27623d)

   __With Capacitor :__
   
   ![Circuit Diagram with Cap](https://github.com/user-attachments/assets/201ca612-e3a9-4918-923c-666fee12ab5d)

      
## 5.  Procedure :

__A. Schematic Setup :__

_1. Circuit Construction :_
       Connect a PMOS transistor in Common Source configuration with the Source tied to $V_{DD}$ and a resistor $R_D$
       at the Drain.

_2. Library Linking :_
      Add the .include directive for the specific technology library (e.g., TSMC 180nm)to utilize realistic device parameters.

_3. Sources :_
      Configure DC supplies for $V_{DD}$ and input biasing, and an AC/Sine source for signal testing.

__B. DC Analysis & Biasing :__
     
_1. Target I<sub>D</sub>:_
     Determine the required Drain current based on the design's power budget ($P = V_{DD} \times I_D$).

_2. Resistor Sizing:_
     Select $R_D$ to set the quiescent output voltage ($V_{out}$) at approximately $V_{DD}/2$ for maximum signal swing.

_3. Operating Point (.op):_
     Iteratively adjust the Transistor Width ($W$) in the simulator until the target $I_D$ is achieved.

 _4. Region Check:_
      Verify the device is biased in the Saturation Region by ensuring $|V_{DS}| \geq |V_{GS} - V_{th}|$.

__C. Transient Analysis (Time Domain)__

  _i. Waveform Observation:_
      Apply a small-amplitude sine wave to the input and observe the output at the Drain.

  _ii. Phase Inversion:_
       Confirm the $180^\circ$ phase shift between input and output, which is characteristic of a CS stage.

  _iii. Voltage Gain:_
       Calculate gain ($A_v$) by measuring the ratio of peak-to-peak output to peak-to-peak input
       ($V_{out(p-p)} / V_{in(p-p)}$).

  __D. AC Analysis (Frequency Domain)__

  _i. Frequency Response:_
       Perform an AC sweep (.ac) to plot the gain magnitude and phase across a wide frequency spectrum.

  _ii. Bandwidth Measurement:_
       Identify the -3dB cutoff frequency to determine the amplifier's effective bandwidth.

  _iii Loading Effects:_
      Repeat the sweep with an added load capacitor ($C_L$) to observe the resulting decrease in bandwidth.
   
 __E. Results Verification__

  _1. Comparative Study:_
      Compare simulated $I_D$, $A_v$, and Power against theoretical hand-calculated values.

  _2. Analysis:_
      Document discrepancies, noting the impact of short-channel effects like Channel Length Modulation ($r_o$).

## 5. Observation :

  ## 1. Without Capacitor :_
      
  __1. DC Analysis :__

  ![DC Operating Point](https://github.com/user-attachments/assets/9db9b549-5df6-491e-8234-db0801788747)

  __2. Transient Analysis :__

  ![Transient Analysis Curve](https://github.com/user-attachments/assets/134c5e2c-ef15-42b0-9c7c-02af0eaa596e)

  __3. AC Analysis :__

  ![AC Analysis Curve of Bandwidth without Cap](https://github.com/user-attachments/assets/9ccd4a95-6bd9-40ab-91d4-f7b3de1aa680)


  ## 2. With Capacitor :

  __1. DC Analysis :__

  <img width="954" height="778" alt="DC Analysis with Cap" src="https://github.com/user-attachments/assets/273ae210-dd9b-4b3c-a725-db0206161243" />
            

  __2. Transient Analysis :__

  ![Transient Analysis Curve with Cap](https://github.com/user-attachments/assets/449a4718-c57d-41bc-bd2d-2f45d07b073f)
       

  __3. AC Analysis :__

   ![AC Analysis Curve of Bandwidth with Cap](https://github.com/user-attachments/assets/49c71337-e5a6-48d8-a561-eb61a140da8a)

  | Parameter | Unit | Theoretical Value | Simulated Value |
  | :--- | :--- | :--- | :--- |
  | **Drain Current ($I_D$)** | &mu;A | 200 | 200.0005 |
  | **Output Voltage ($V_{out}$)** | V | 0.9 | 0.900022 |
  | **Transconductance ($g_m$)** | A/V | $7.843 \times 10^{-4}$ | $7.84313 \times 10^{-4}$ |
  | **Voltage Gain ($A_v$)** | dB | 10.954 | 10.422 |
  | **Bandwidth (without $C_L$)** | GHz | 18.23 | 18.226 |
  | **Bandwidth (with $10\text{pF}$ $C_L$)** | MHz | 4.01 | 4.0059 |
  | **Power Dissipation ($P$)** | mW | 0.36 | 0.36 |

        

## 6. Calculations :

__A. Power and Resistor Design__

_1. Power (P)_:
> $P = V_{DD} \times I_{D} = 1.8V \times 200\mu A = 0.36mW$.

_2. Load Resistor (R<sub>d</sub>):_ 
> $R_{d} = \frac{V_{DD} - V_{out}}{I_{D}} = \frac{1.8 - 0.9}{200\mu A} = 4.5k\Omega$

__B. Transistor Sizing ($W$) Iterations__

To achieve $I_D = 200\mu\text{A}$, the width was optimized through simulation:

At $W = 2.84\mu\text{m} \rightarrow I_D = 115.2\mu\text{A}$.

At $W = 5.18\mu\text{m} \rightarrow I_D = 200.124\mu\text{A}$.

__Final Value: $W = 5.18144\mu\text{m} \rightarrow I_D = 200.005\mu\text{A}$.__

__C. Gain Analysis (Transient)__

$V_{in(p-p)} = 19.218\text{mV}$.

$V_{out(p-p)} = 63.832\text{mV}$.

Simulated Gain ($A_v$): $\frac{63.832\text{mV}}{19.218\text{mV}} = 3.3214\text{ V/V}$.

In dB: $20 \log(3.3214) = 10.4265\text{dB}$.

__D. Theoretical Gain__

$g_m = \frac{2 I_D}{V_{SG} - |V_t|} = \frac{2(200\mu\text{A})}{0.9\text{V} - 0.39\text{V}} =7.843 \times 10^{-4}\text{ A/V}$.

$A_{v(theory)} = g_m \times R_d = (7.843 \times 10^{-4}) \times 4.5\text{k}\Omega = 3.529\text{ V/V} = 10.954\text{dB}$.


## 7. Result and Inference

__1. Design Validation:__

The circuit successfully achieved the target Q-point ($200\mu\text{A}, 0.9\text{V}$)
 using $R_d = 4.5\text{k}\Omega$ and $W = 5.18144\mu\text{m}$.

__2. Power:__

The design consumed only $0.36\text{mW}$, staying well below the $1\text{mW}$ constraint.

__3. Error Analysis:__

There is a minor $4.8\%$ difference between theoretical ($10.95\text{dB}$) and simulated ($10.42\text{dB}$) gain.
This is due to Channel Length Modulation ($r_o$), which reduces output impedance in short-channel devices.

__4. Capacitance Effect:__
  
  The addition of a $10\text{pF}$ load capacitor reduced the bandwidth from $18.22\text{GHz}$ to $4.00\text{MHz}$.
  This proves that external load capacitance is the dominant factor in high-speed signal degradation.
