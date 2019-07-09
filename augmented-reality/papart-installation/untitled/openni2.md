# OPENNI2

## Linux

1. Go to [https://orbbec3d.com/develop/](https://orbbec3d.com/develop/) and download the latest OpenNI version
2. Unzip the download file
3. Go to `Linux/YourLinuxVersionFolder/Samples`
4. Test your camera by running `./NiViewer`  _The binary file may not be executable at first, if so try to run `chmod +x NiViewer` to make it executable_
5. You should be able to preview the **color**, **depth**, and **IR** streams of your camera.

If the camera is working you can then use **OPENNI2** as your camera driver however you still to include the library into your processing sketchbook folder if it has not been done before. Modify the `cameraConfiguration.xml` file to look like so: 

{% code-tabs %}
{% code-tabs-item title="cameraConfiguration.xml" %}
```markup
<?xml version="1.0" encoding="UTF-8"?>
<Calibration>
  <Camera CameraFormat="rgb" CameraName="0" CameraType="OPENNI2"/>
</Calibration>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

As previously stated **CameraFormat** could also be set to `depth` or `ir`.

## Windows

## OSX

See this forum thread [http://natar.io/t/orbbec-astra-for-macosx-users/73/2](http://natar.io/t/orbbec-astra-for-macosx-users/73/2)

