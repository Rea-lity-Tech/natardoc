# OPENCV

## Linux

1. Open up a **shell**
2. List the available video devices `$ ls /dev/ | grep video`
3. Choose your video device from the output and remember its number

Modify the `cameraConfiguration.xml` file to look like so: 

{% code-tabs %}
{% code-tabs-item title="cameraConfiguration.xml" %}
```markup
<?xml version="1.0" encoding="UTF-8"?>
<Calibration>
  <Camera CameraFormat="rgb" CameraName="0" CameraType="OPENCV"/>
</Calibration>

```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
Do not forget to replace the name`0` by your own device number as listed by the `ls` command.
{% endhint %}

## Windows

## OSX

