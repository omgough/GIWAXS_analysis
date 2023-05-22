# giwaxs_analysis
Scripts for analysing GIWAXS data.

**Prerequisites**

1. Have following packages installed:

required: ```pyFAI```, ```pandas```, ```fabio```, ```matplotlib```

optional: ```plotnine```, ```fityk```

2. Generate the calibration files using pyFAI - in terminal run ```pyFAI-calib2``` to open GUI. 
  - on 'Experiment settings', input beam energy, calibrant type, detector type, and calibration image file (click next)
  - In 'Mask' tab, mask dead pixels by hand with pen tool or mask below a certain threshold. If detector is in modules, the spaces between modules should be masked. 
  - **Save mask file!** Click on save button in mask sub-tab on right hand side of GUI. (click next)
  - In the 'Peak picking' tab, starting from the inner-most ring and working outwards, pick around 10 peaks. Make sure they are nicely fitted and erase any points that don't sit directly on a ring, can add more points to a ring. 
  - **Save picked rings** - this is important if you need to go back and recalibrate. (click next)
  - Check 'Geometry fitting', the distance in the geometry sub-tab should correspond with the detector distance in log book. All the rotation angles should be very close to zero. 
  - Set Rotation 1, 2, 3 to zero degrees and click 'Fit'. This shouldn't change the fit much - it means we are assuming the detector is completely flat.
  - Finally, on 'Cake and Integration', check the intensity as a fn of 2 theta and make sure the peaks are aligned. Now you can do **Save as PONI file...** (point of normal incidence).
  - The PONI file defines the geometry of the setup and should be imported along with the mask file in every script you run with data processing.
