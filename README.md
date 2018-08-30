# Wing_Track_Fixer
Matlab App that Manually Fix the Error in Wing Tracks

The wing tracking results generated from https://github.com/kristinbranson/cbtrack/tree/master/simplewing may not be 100% correct.
This app is aimed to fix the errors in the output from simplewing.

This matlab app runs on Matlab 2018a or above only. The version which is compatible with 2017b is also provided.

Parameters that can be Fixed:
  wing_anglel
  wing_angler
  nwingsdetected
  wing_trough_angle
  xwingl
  xwingr
  ywingl
  ywingr

Limitations:
  1. Currently only supports Male fly. This limitation can be easily fixed.
  2. Video viewing is based on frame by frame image viwing, which may not be smooth. 
     It is possible to use ctrax or JAABA as alternative video player.
  3. No automated potential error detection is included, even though it shows up in the app.
     This feature will be added depending on the needs. 

Format:
  1. fmf format video and the tracking results should be placed under the same folder. 
  2. Video should be named 'video.fmf'
  3. Tracking results shoule be named 'video.mat'

How to Use:
Startup Preparation:
  1. From drop down menu, use 'Browse' button to select the folder where the video and tracking file are located.
  2. Video Length indicates the length of the video.
  3. From drop down menu, use 'Start' button to call out the video viewer with tracking information on top of it.
   It is also possible to change the number in 'frame_index' to call out certain frame of the video with tracking info.

To Fix Errors Frame by Frame:
  If the wings are open and the angle is not captured correctly:
    1. Switch the 'WingDetected' switch to 'Two'.
    2. Drag the orange and blue line to match the angle of the wing. 
     The length of the dragged line does not matter since it will be adjusted to the average wing length based on the tracking info.
    3. The green line indicate the wing_trough_angle, which will be updated automatically based on the fixed angle of both wings.
    4. Click 'Fix' button.

  If the wings are closed and the angle is not captured correctly:
    1. Switch the 'WingDetected' switch to 'One'.
    2. Click 'Fix' button.

To Fix Errors in Batch:
  If the wings are opening and closing on a constant rate:
    1. Switch the 'WingDetected' switch to 'Two'.
    2. In the video viewer, pull out the beginning frame and drag the wing line to the correct position.
    3. Click the 'Set' button next to 'Begin' number box in the interpolation panel.
    4. In the video viewer, pull out the ending frame and drag the wing line to the correct position.
    5. Click the 'Set' button next to 'End' number box in the interpolation panel.
    6. Click the 'Interpolate' button.
    
  If the wings are closed throughout a period of time:
    1. Switch the 'WingDetected' switch to 'One'.
    2. Type in the beginning frame index in 'Begin' number box in the interpolation panel.
    3. Type in the ending frame index in 'End' number box in the interpolation panel.
    4. Click the 'Interpolate' button.

To Save Progress:
  1. Click 'Quick Save' switch. When the save is completed, the switch will go back to 'saved' position from 'saving' position.
     This will create a temporary file in the folder, which will not be deleted upon exit of the app.
     The temporary file will be overwritten each time 'Quick Save' switch is clicked.
  2. From drop down menu, use 'Save as' button to name a file and save as .mat format.
  
To Resume Progress:
  1. Every time when a video folder is selected through 'browse' button. Temporary save file will be loaded if it exist.
     If temporary save file cannot be found, 'video.mat' will be loaded.
  2. To load a save file saved through 'save as', click 'Load' button from drop down menu after a video folder has been selected. 



fmf file reading handling is credited to https://github.com/kristinbranson/cbtrack_GUI/tree/master/filehandling

code for arrow drawing to indicate fly orientation is found online.
