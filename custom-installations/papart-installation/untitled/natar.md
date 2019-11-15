# NATAR

## Linux

1. Download and install [Redis](https://redis.io/)
2. Download and install \(`mvn install`\) [natar-core](https://forge.pole-aquinetic.net/nectar-platform/natar-core), [natar-apps](https://forge.pole-aquinetic.net/nectar-platform/natar-apps).
3. Download and package \(`mvn package`\) [natar-multi-camera-server](https://forge.pole-aquinetic.net/nectar-platform/natar-multi-camera-server) \(driver\) and [natar-camera-client](https://forge.pole-aquinetic.net/nectar-platform/natar-camera-client) \(our test application\). 
4. Start a **Redis** server
5. Run the server application:`$ java -jar natar-multi-camera-server-0.1-jar-with-dependencies.jar --driver $driver --device-id $id --format $format --output $name`
   1. `--driver, --device-id, --format` refers to the same option as in the `cameraConfiguration.xml` file
   2. `--output` is specific to this program and it a key referring to where the camera driver will be outputting the camera frames it is grabbing.
   3. Replace `$driver, $id, $name` by real values as explained above.
6. Run the client application and check that everything is working:  `java -jar natar-camera-client-0.1-jar-with-dependencies.jar --input $name`
   1. `--input`  as opposed to the `--output` option of the server program is a key referring to where the application should expect to find camera frames data.

{% hint style="warning" %}
When building `natar-multi-camera-server` and `natar-camera-client`it will build 2 jars per project, one classic jar and one jar named `$project-jar-with-dependencies.jar`. This second version embeds all the dependencies in a single jar as the name states thus making it easier to use.   
**Be careful to use that version instead of the classic one.**
{% endhint %}

Once everything is perfectly working you can configure you `cameraConfiguration.xml` file for **PapARt** to use this new sort-of camera driver like so:

{% code title="cameraConfiguration.xml" %}
```markup
<?xml version="1.0" encoding="UTF-8"?>
<Calibration>
  <Camera CameraFormat="rgb" CameraName="$name" CameraType="NECTAR"/>
</Calibration>
```
{% endcode %}

{% hint style="info" %}
Natar driver does not currently support IR **CameraFormat**.  
Also CameraName has to match the `--output`value represented by the variable `$name`in this post.
{% endhint %}



