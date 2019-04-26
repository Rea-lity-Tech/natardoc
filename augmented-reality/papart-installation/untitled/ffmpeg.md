# FFMPEG

## Linux

1. Open up a **shell**
2. List your compatible devices `$ v4l2-ctl --list-devices`
3. Test your device `ffmpeg -f v4l2 -i /dev/video0 webcam-test.avi` .  **Replace** `/dev/video0` with your own device name.
4. Check out the generated webcam-test.avi file

{% hint style="info" %}
For more information on how to use **FFMPEG** for video capture please refer to this [article.](https://trac.ffmpeg.org/wiki/Capture/Webcam)
{% endhint %}

If the camera is working you can then use **FFMPEG** as your camera driver. Modify the `cameraConfiguration.xml` file to look like so: 

{% code-tabs %}
{% code-tabs-item title="cameraConfiguration.xml" %}
```markup
<?xml version="1.0" encoding="UTF-8"?>
<Calibration>
  <Camera CameraFormat="" CameraName="/dev/video0" CameraType="FFMPEG"/>
</Calibration>

```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
Do not forget to replace the name`/dev/video0` by your own device name as listed by the `v4l2-ctl` command.
{% endhint %}

## Windows

## OSX

