# Control-System-Simulator-with-PD-Regulator

**Task description**
The design task was to create a system simulator with an object given the transfer function G(s) = (a1*s+a0)/(b2*s^2+b1*s+b0 ) with a PD controller closed in a negative feedback loop. The program allows you to obtain time responses for three different stimulations.

**A brief description of the GUI and the most important functions:**
The user can enter each transmittance coefficient and controller parameters (Kp - inertial gain, Kd - differential gain, Tp - inertial time constant, Td - time constant related to differentiation) Note - Tp and Td are implemented only for counting transmittance, for responding to no more arousal.

![image](https://github.com/Gawendz/Control-System-Simulator-with-PD-Regulator/assets/105167719/5876aa07-fce4-45a3-af84-19fe2acf5455)

To calculate the transmittance of the system, I used the NumPy library. In the transmittance() function, the transmittance coefficients and controller parameters are taken and the numerator and denominator of the transmittance of the closed system are created:

G(s) = ((Kd*s+Kp)*(a1*s+a0)*e^(-Tp*s))/((b2*s^2+(b1+Kd*s)*s+(b0+Kp)*(Td*s+1)) 

Based on the introduced values ​​of transmittance coefficients and PD controller parameters, a differential equation describing the system and excitation is defined. The initial value for the system response is determined. Then, in the loop for each time step 'i', the value of the derivative of the function, i.e. the error, is calculated based on the difference between the excitation and the current response of the system. The value of the system's response for the next time step is approximated by adding the product of the time step and the derivative to the previous response value, and the obtained response of the system is recorded in a table that will be used to draw a graph.

**For example, for a1=1 and a=2:**
![image](https://github.com/Gawendz/Control-System-Simulator-with-PD-Regulator/assets/105167719/914d6457-4948-491b-813b-24bb7e87db07)

**An example of the system's response to sine at Kp = 1 and Kd = 0.5:**
![image](https://github.com/Gawendz/Control-System-Simulator-with-PD-Regulator/assets/105167719/65a1be2b-8e2f-4e27-a0a4-67c614e5e412)


