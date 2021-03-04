# Head-and-Eye-Gaze-Robot-Control

Link to the paper will be given here as soon as it is online.

This repository holds data from various trials for head- and eye-gaze robot control (accuracy wise). This repository will also host ROS based software parts to enable eye-gaze point estimation using Pupil Labs software inside ros and merge it onto the infrared data streams.

The data is structured as follows:
head_xyz.mat - These files contain the aligned and pre-processed data points from a complete set of head-gaze estimation results benchmarked against a Qualisys Motion Capture system.
Struct with fields:
  - angles 
    - rmse_mean_inertial - Mean Inertial only orientation estimation results for the complete trial
    - rmse_mean_vis_inertial - Mean Visual-Inertial orientation estimation results for the complete trial
    - rmse_mean_vis - Mean Visual only orientation estimation results (not recorded for every trial)
  - trajectory
    - rmse_mean_inertial - Trajectory from visual only position estimation (despite the confusing name)
  - eye_struct
    - mean_e - Mean head-gaze position errors for each of the 24 targets
    - stdev - Standard deviations for the before mentioned trials
    - assets - Offset of subject after new calibration of qualisys system (x,y position and pitch and yaw angle differences to align coordinate systems)
    - gazeDiffpts - Raw Gaze Points recorded for each individual target point (contains 24 cells where each cell contains a matrix n x 3)

gaze_xyz.mat - The same as head_xyz.mat but the gaze points are recorded using eye-gaze

robot_trajectory_xyz.mat - The same as head_xyz.mat but the results are from a human-robot control expirement - The accuracy is benchmarked against the robots tcp.
