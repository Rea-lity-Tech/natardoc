# PROCESSING

## Linux

1. Open up a **shell**
2. Install **GStreamer 0.10:** `gstreamer0.10, gstreamer0.10-good, gstreamer0.10-bad`
3. Test your device by running the `GettingStartedCapture` processing example under `Examples -> Libraries -> Video -> Capture -> GettingStartedCapture`
4. Make sure it is working.
5. Get the device name in the list given by the example.

Modify the `cameraConfiguration.xml` file to look like so: 

{% code title="cameraConfiguration.xml" %}
```markup
<?xml version="1.0" encoding="UTF-8"?>
<Calibration>
  <Camera CameraFormat="" CameraName="/dev/video0" CameraType="PROCESSING"/>
</Calibration>

```
{% endcode %}

{% hint style="warning" %}
Do not forget to replace the name`/dev/video0` by your own device name as listed by the processing example `GettingStartedCapture`
{% endhint %}

## Windows

## OSX

