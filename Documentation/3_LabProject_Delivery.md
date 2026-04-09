![University of Barcelona Logo](././Images/3D_Orientation/UB.png)
 
## GRUP 1: SEMINARI D'EINES D'ENGINYERIA BIOMÉDICA
---
 
## INDEX
 
1. What we have done
2. Proceeding with the suggested questions
3. Final conclusions
 
---
 
## 1. What we have done
 
Once the hardware setup was completed, the first step was to configure the IP address of the Endo-module to the one corresponding to our group, G1.
 
The first operating performance diagnostic provided an output that indicated a failure in the connection between the IMU sensor and the Endo-Module. No data was being transmitted, and the system was not responding as expected. We reviewed the uploaded program and made sure there were no errors in the code or in the IP address configuration. After realising all other groups were having the same connection failure, it became clear that the issue was not isolated to our setup. The source of the error was the router, _Robotics\_UB_. After rebooting the router, the Python script was run again and the connection was established correctly.
 
Once the connection was stable, we were able to visualize the selected 3D object (initially the `plane`) moving in real time in response to the movement of the Endo-module. By applying corrections, the movements performed on the Endo-module matched those observed on the 3D object in RoboDK.

Initially, we used a plane as the visualized object and later changed it to a surgical needle to better represent a medical application.
 
### Code changes made
 
To adapt the program to our group setup and ensure correct communication and visualization, we made the following changes:
 
- **Device ID update (`main.cpp`):** Changed the device identifier from `"G5_Endo"` to `"G1_Endo"` to match our group.
- **Receiver IP update (`main.cpp`):** Changed the receiver computer IP address from `192.168.1.55` to `192.168.1.15` so the IMU data was sent to the correct computer.
- **Target device update (`Receive_data_RPY_IMU_world.py`):** Changed the target device from `"G5_Endo"` to `"G1_Endo"` so the script received data from our Endo-module.
- **3D object update (`Receive_data_RPY_IMU_world.py`):** Changed the visualized object in RoboDK from `"plane"` to `"surgical_needle"` to visualize and orient the needle correctly.
 
<img width="997" height="581" alt="image" src="https://github.com/user-attachments/assets/ffa38885-1d2c-4686-a600-324bc4e1d4d8" />
 
<img width="1088" height="461" alt="image" src="https://github.com/user-attachments/assets/d5c87a92-f73d-4bc4-8b77-b40515d998fc" />
 
---
 
## 2. Proceeding with the suggested questions
 
### Is the `plane` 3D object in RoboDK moving properly?
 
Initially, the plane was moving in real time in response to the IMU sensor data. However, the movement was not properly aligned with the real orientation of the sensor.

This means that although the object was moving, it was not moving correctly, since the axes of the virtual object did not match those of the IMU. After applying orientation corrections, the movement became accurate and consistent with the physical motion.
 
### What did we do to properly verify the orientation angles Roll, Pitch, and Yaw?

We realised that the orientation of the virtual object did not match the actual physical orientation of the IMU sensor. To solve this issue, we performed two types of adjustments: 
* First, we applied a **north orientation** correction to align the reference direction of the sensor with the expected world reference in roboDK.
* Second, a **3-axis orientation correction** was performed to ensure the Roll, Pitch, and Yaw rotations from the IMU matched the axes of the 3D object. By doing this, the movements performed on the Endo-module matched the ones observed on the plane in roboDK.
 
### What did we have to change in the Python code to switch the 3D object to `surgical_needle`?
 
In the file `Receive_data_RPY_IMU_world.py`, we located the line where the 3D object name was defined and changed it from `"plane"` to `"surgical_needle"`. This single change was sufficient for RoboDK to load and animate the surgical needle instead of the plane, while keeping all the orientation logic and IMU data reception intact.
 
---
 
## 3. Final conclusions
 
The first conclusion we derived was the importance of not trusting raw simulation output without verification. As described above, we had to adjust the axis mapping in the 3D visualization to match the IMU sensor's physical axes. If we had not done this, we would have been visualizing movements that did not correspond to what was actually happening on the Endo-module. This reinforced a key engineering principle: **always validate that simulation results reflect reality before drawing any conclusions**.
 
Regarding the applicability of these tools in our **avant-projecte**, a *Postural Correction Chair*, we concluded that an IMU sensor could be highly useful for tracking the inclination or movement of the user's spine in real time. By defining threshold values for Roll, Pitch, and Yaw, the system could emit an alert whenever the user's posture deviates beyond acceptable limits. The lab experience gave us a practical understanding of how to configure and calibrate such a sensor, which is directly transferable to our project.

Regarding the TFG, some of us are interested in the biomechanics field of the Biomedical Engineering degree. A quite ambitious TFG proposal related to that field could be to develop a prosthesis for any specific application. This would be much more complex than what we did on this session, but the skills we acquired are some of the basis that we need to build more complex hardwares. An IMU sensor could easily be a fundamental part of a prosthesis where we want to track the orentiation and rotation of each joint in the artificial extremity, because this is essential to know the limb's state and position.    
 
More broadly, we adquired skills in this session, such as wireless sensor communication, real-time 3D visualization, and axis calibration, that are relevant to a wide range of engineering applications, from robotics applied to medicine to wearable monitoring systems.
 
![Image 2026-03-19 at 12 45 30](https://github.com/user-attachments/assets/c953e124-dbc5-4198-bee5-bca850a71d1c)

---
Members:
- Núria Cerón
- Carlota Garrido
- Martina Viñolas
