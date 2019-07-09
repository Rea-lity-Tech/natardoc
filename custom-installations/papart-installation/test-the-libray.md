# Test the libray

## Step 2: Libraries test.

Launch the example `Sketchbook -> PapARt-examples -> first-examples -> Debug -> simple`. Run the example. You might get warnings:

`No library found for org.bytedeco.javacpp.opencv_core`

Please ignore them, these is an [issue open](https://github.com/poqudrof/PapARt/issues/7) to fix this. It is just debug text.

## Step 3: Camera test.

1. Print the markerboard: You can find it in `libraries\PapARt\data\markers\A4-default.pdf` or online on github: [download link](https://github.com/poqudrof/PapARt/raw/master/papart/data/markers/A4-default.pdf).
2. Launch the example `Sketchbook -> PapARt-examples -> first-examples -> Camera -> SeeThrough`. Run the example, and show the printed sheet in front of the camera.

You can download presets for many cameras and copy it to `sketchbook/libraries/PapARt/data/calibration/cameraConfiguration.xml` \(right click, save as\):

* [Realsense](http://dist.rea.lity.tech/libs/calibrations/realsense/cameraConfiguration.xml). 
* [Many driver \(OpenCV\)](http://dist.rea.lity.tech/libs/calibrations/opencv/cameraConfiguration.xml). 

The configurations are discussed on the [camera library usage thread](http://forum.rea.lity.tech/t/use-papart-as-a-camera-library/50/1).

#### Possible issues:

**Q:** The app crashed, it could not start the camera. **A:** You need to check the cable, and choose the right driver, as explained on [this thread](http://forum.rea.lity.tech/t/use-papart-as-a-camera-library/50).

**Q:** I have two cameras, and I want to use the other one. **A:** You can specify the camera name, or number depending on the driver. It is explained on [this thread](http://forum.rea.lity.tech/t/use-papart-as-a-camera-library/50).

**Q:** I did not try yet, is my camera supported ? **A:** Yes most likely.

### Conclusion

Now you have a fully working PapARt system for "see through" applications. You can try the other "Camera" examples in `Papart-examples -> First examples -> Camera`. If you want a deeper view of PapARt possiblites you can look at `PapARt -> features -> advancedUses`. Most of the adanced examples use a single webam for compatibility.

### Going further

AR applications in PapARt follow a particular design, [the tutorials](http://forum.rea.lity.tech/c/papart-tutorials) are here to help. We encourage you to read about the [Papart helper](http://forum.rea.lity.tech/t/papart-helper-in-papart/42), the [display model](http://forum.rea.lity.tech/t/display-model-in-papart/40), and the [PaperScreen](http://forum.rea.lity.tech/t/paperscreen-model-in-papart/39) abstraction. The next step is to calibrate your camera, a link to the calibration guide will be posted here.

