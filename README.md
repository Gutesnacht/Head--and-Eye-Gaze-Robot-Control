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

The repository also contains the raw data. This data has the following form:
SLAM_Quali_recording_xyz.csv 
 - Q1_w, Q2_w, Q3_w, Q4_w - Inertial only orientation Quaterions
 - Q1_fused, Q2_fused, Q3_fused, Q4_fused - Inertial only orientation Quaterions
 - Q1_Quali, Q2_Quali, Q3_Quali, Q4_Quali - Inertial only orientation Quaterions
 - x_fused, y_fused, z_fused - Visual Position Estimation 
 - x_quali, y_quali, z_quali - Qualisys Motion Caputre Position Estimation 
 - x_target, y_target, z_target - Gaze Point estimation (either head or eye gaze)
 - in_surface - Toggle if gaze is in surface (toggled from human)
 - QTimeSec_q, QTimeNSec_q - Unix Timestamps
 - (some have optional further fields):
    - vslamQ1, vslamQ2, vslamQ3, vslamQ4 - Visual only orientation Quaternions
    - fused - Flag to indicate wheter the SLAM orientation is fused with inertial or not.
 
 Ground Truth Target Position estimates as .mat
  - 24 Target positions (in x,y,z) - adapted using the assets field to account for orientation and position changes from calibration errors.
