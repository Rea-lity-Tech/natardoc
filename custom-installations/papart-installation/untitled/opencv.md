# OPENCV

## Linux

1. Open up a **shell**
2. List the available video devices `$ ls /dev/ | grep video`
3. Choose your video device from the output and remember its number

Modify the `cameraConfiguration.xml` file to look like so: 

{% code title="cameraConfiguration.xml" %}
```markup
<?xml version="1.0" encoding="UTF-8"?>
<Calibration>
  <Camera CameraFormat="rgb" CameraName="0" CameraType="OPENCV"/>
</Calibration>

```
{% endcode %}

{% hint style="warning" %}
Do not forget to replace the name`0` by your own device number as listed by the `ls` command.
{% endhint %}

There is no concrete out of the box example to test out your camera with **OpenCV** but you can find several tutorials online on how to do it: [Getting Started With Videos \(Python\)](https://docs.opencv.org/3.0-beta/doc/py_tutorials/py_gui/py_video_display/py_video_display.html)

## Windows

## OSX

