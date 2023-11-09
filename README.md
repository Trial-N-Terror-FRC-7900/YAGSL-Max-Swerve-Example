# BASED ON: 2023 Yet Another Generic Swerve Library (YAGSL) Example project

YAGSL Example: https://github.com/BroncBotz3481/YAGSL-Example

## Disclaimer

This wasn't originally supposed to be a good example for other teams, but we have no issue with it becoming that. We will try our best to keep the Main workng properly, but if you have issues please open an issue. 

# Tips and Tricks

### Encoder Offsets
Absolute Encoder offsets should be done on the sparkmaxes directly. Ignore the offsets in the JSON config files. We initally set the offsets using the MaxSwerve jigs, but then adjusted the offsets in the Rev Hardware Client in the advanced tab. Adjust in +/-0.25 increments until all the modules will run in the same direction. Using YAGSL currently may cause the modules to jitter. We plan to put in sparkmax offsets using the RevLib Directly. 

### Joystick Controls
The default controls for turning has the right joystick point towards the direction you want the robot to face, so it departs from the MaxSwerve Example Code.

### NavX Inverted IMU
We have noticed that if the robot drives forward opposite to the direction expected by the NavX the inverted IMU will have to switched from True (technically proper) to False.

### Sparkmax IDs
CAN IDs past 40 seem to cause issues for YAGSL. 

### Matching Real Life to what is seen in PathPlanner
If the robot does not drive the correct distance that PathPlanner is attempting to go to the Wheel Diameter maybe needed to be adjusted to meet the correct distances. 
If the robot does not follow the Path, but PathPlanner believes it does adjust the PID Constants in Constants.java


# Fixed in this example but still of note

### NavX Quaternions Issues
As of the 2023.0.3 Version of the NavX lib there is issues with how the NavX reports quaternions. So in our example we multiply them by 0.5 which fixed the issues for us. CD Thread detailing more about the problem and potential fixes from the NavX team: https://www.chiefdelphi.com/t/navx-quaternion-units/443538?u=technologyman00
