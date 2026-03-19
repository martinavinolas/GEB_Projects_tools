![University of Barcelona Logo](././Images/3D_Orientation/UB.png)

## SEMINARI D'EINES D'ENGINYERIA BIOMÉDICA: DELIVERY GRUP 1


INDEX:

1. Our first operating performances diagnostic, 
2. The corrections we have made in the code
3. Your final conclusions 


### **1. Our first operating performances diagnostic**
We performed a set of operations in order to make the sytem work properly. 

Once the hardware setup was completed, the first step was to configure the IP adress of the Endo-module to the one corresponding to our group, G1.
The first operating performance diagnostic provided an output that indicated a failure in the connection between the IMU sensor and the Endo-Module. No data was being trasmitted, and the system was not responding as expected. 
We reviewed the uploaded program and made sure there were no errors in the code or in the IP adress configuration. After realising all other groups were having the same connection failure, it became clear that the issue was not isolated to our setup. The source of error was  the router, _Robotics_UB_. After rebooting the router, the Python script was ran again, and the connection was stablished correctly.

Once the connection was stable, we were able to visualize the selected 3D object, which was at first the plane, moving in real time in response to the movement of the Endo-module. However, we realised that the orientation of the virtual object did not match the actual physical orientation of the IMU sensor. 
To solve this issue, we performed two types of adjustments. First, we applied a **north orientation** correction to align the reference direction of the sensor with the expected world reference in roboDK. Second, a **3-axis orientation** correction was performed to ensure the Roll, Pitch, and Yaw rotations from the IMU matched the axes of the 3D object. By doing this, the movements performed on the Endo-module matched the ones observed on the plane in roboDK.


### The corrections we have made in the code

idees:
- lu del nom del grup
- ip del ordinador
- objecte a visualitzar 



### Our final conclusions 

The first conclusion we derived was to not trust every raw output we obtain from our simulation. As we mentioned, we had to adjust the axis in the 3D visualization and make them match those of our IMU sensor. If we hadn’t done this, we could have been visualizing a movement in the plane that didn’t correspond to the one we were applying to the endo-plate. We must always verify that our results are reliable, even if that means we have to make modifications in the simulations.

Furthermore, we tried to give a thought on how our Group Project could benefit from the use of an IMU sensor (we aim to develop a “Postural Correction Chair”). We concluded that an IMU could be useful to track the movement or inclination of the user’s spine and emit an alert when the measured values surpass a threshold.
![Image 2026-03-19 at 12 45 30](https://github.com/user-attachments/assets/c953e124-dbc5-4198-bee5-bca850a71d1c)


