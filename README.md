**#Rubik's Cube Scanner and Solver (RubiBot)**

This project is a hybrid software-hardware system designed to scan, model, and physically solve a 
3X3 Rubik's Cube. It integrates a computer vision scanning pipeline that calculates an optimal solving sequence with an Arduino-controlled robotic solver that physically executes the moves.

#Core Components:
1. Software Pipeline:
   Ambient Light Calibration: Accounts for varying illumination by scanning a solved cube first. The script extracts baseline median HSV (Hue, Saturation, Value) values from defined patches on each facelet.
   Weighted HSV Classification: Detects scanned facelet colors using a custom weighted Euclidean distance metric to reduce misclassifications caused by shadows.
   
3. Algorithmic Solving:
   Translates the 54 facelet readings into a standard string and utilizes the Kociemba two-phase algorithm to compute the shortest move sequence.
   
5. Hardware Assembly:
   Microcontroller: An Arduino Mega 2560 processes sequence execution commands received via serial communication from the host computer.
   Actuators: High-torque stepper motors (NEMA 23) handle the mechanical rotation of individual cube faces.
   Structure: Custom CAD-modeled mechanical turning arms and motor mounts are designed into 3D-printable STL files to grip and turn the physical cube.

#Project Status
1. Current Progress: The software pipeline is complete. The Python script is fully functional and successfully calibrates color spaces, maps scanned faces via webcam, handles light-variation warnings, and queries the                            solver to generate optimal outputs.
2. Future Work: Current efforts are focused on the hardware phase. This includes printing the physical mounts and arms using the designed STL files, assembling the stepper motor hardware, and writing the C++ Arduino                        firmware to convert computed solution strings (e.g., U2 R L') into coordinated motor steps.

#Software Setup and Running
Install dependencies:
code
Bash
pip install opencv-python numpy kociemba
Run the application:
code
Bash
python main.py
Follow the on-screen prompts to calibrate the solved cube and scan your scrambled cube.
