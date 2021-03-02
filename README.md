# Allen Sun - MSE 2202A Lab 5 Submission

## Links to Lab 5 Demo Videos
Level 1: https://photos.app.goo.gl/gPdGXYfkVTumBiEfA

Level 2: https://photos.app.goo.gl/7RJGssCpzx5FDSe88

## Remarks

*Note*: this repository was duplicated from the original repo, **MSEbot_basecode**. The changes to the file `MSEbot_basecode.ino` were pushed while programming.

For this lab exercise, I was able to successfully complete the Level 1 task. I was unable to fully satisfy the requirements of the Level 2 task, and did not have sufficient time to work on Level 3.

### Code and troubleshooting
My approach to the tasks involved estimating the number of encoder ticks to travel a measured distance. The parameters passed into `ENC_SetDistance()` required careful tuning to result in the desired distance travelled. As well, I attempted to straighten the robot's path by decreasing the right wheel speed (`CR1_ui8RightWheelSpeed`) relative to the left wheel speed. This somewhat worked, however the robot's path still varied from run to run. 90 degree turns were calibrated by adjusting encoder tick values to be sent into `ENC_SetDistance()`.

### Next steps
- Experiment with the acceleration parameters in `Encoder.h` to achieve straighter and more consistent motion.
- Experiment with using the beacon to focus the robot towards the target destination -- see pseudocode below.

### Pseudocode for beacon localization in Level 2
```
main timer loop {
  switch (CR1_ucMainTimerCaseCore1) {
    switch (ucMotorStateIndex) {
      case located after the robot passes the obstacle:
      {
        if CR1_ui8IRDatam = letter U {
          // Move to the next case, since the bot is oriented towards the target
        }
        
        // With the help of timing variables, spin the robot around 30 degrees left and 
        // 30 degrees right (relative to original orientation). Spin in roughly 5 degree 
        // increments during each loop through the main timer. Stop spinning as soon as
        // the letter U byte is detected by the IR sensor, and continue to the next case 
        // as nornal.
        
        break;
      }
    }
  }
}
```
