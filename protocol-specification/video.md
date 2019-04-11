# Video

### Reading video

#### Objective: Read an image from camera0 

The camera client connects to Redis and can read the `camera0`  key with at **GET** request to retreive the image data. The image data is store in RGB8 format. It is the only specified for now. 

The resolution can be accessed by the keys: `camera0:width` , `camera0:height` . 

#### Objective: Read a video stream from camera0. 

The camera service notifies the client by outputting a **PUBLISH** command to the `camera0` key. In order to get this information you have to **SUBCRIBE** to `camera0`. This command contains and id of frame \(`timestamp` and `imageCount`\) in JSON. At each new publish, the data in the image was updated right before, you can retreive it with a **GET** command as explained previously.

### Writing video

You need to first set the parameters:  `width`, `height`, `channel` and `pixformat`. Then you can send the image's raw RGB8 data with a **SET** command. When you send a video stream, you can **PUBLISH**  to the `camera0`  key with a JSON that contains the new frame information \(`timestamp`, `imagecount`\). 

### Specification

The name of the keys are defined in a [Google doc](https://docs.google.com/spreadsheets/d/1BCS4Yxje_Yz82fS1PnsAINnBOYi7MSG-mXJhTcbdIEI/edit?usp=sharing), and the whole process can be visualized in this image: 

#### Video Protocol specification \([Google doc](https://docs.google.com/spreadsheets/d/1BCS4Yxje_Yz82fS1PnsAINnBOYi7MSG-mXJhTcbdIEI/edit?usp=sharing%20)\). 

![Video specification](https://www.lucidchart.com/publicSegments/view/2d875a36-225a-4d61-88c0-1680673c4286/image.png)









