---
description: Efficient point cloud rendering in Processing.
---

# Simple Point Cloud

## Description

This library renders point cloud in an efficient way in OpenGL and works for Processing.  It is created to render 300k+ points with the points changing 30 times a second for depth sensors like Kinect.

Download the library: [`SimplePointCloud`](https://github.com/Rea-lity-Tech/SimplePointCloud/releases/download/1.0/SimplePointCloud.tgz)

#### Use case

You can use it directly to do generative art. We created two examples that performs well with 100k points. Here is a simple example with 50k points: 

{% code-tabs %}
{% code-tabs-item title="cloud.pde" %}
```java
import tech.lity.rea.pointcloud.PointCloud;
import tech.lity.rea.pointcloud.DepthPoint;
import toxi.geom.*;
import peasy.*;

PeasyCam cam;
PointCloud pointCloud;
int nbPoints = 500;

void settings() {
    size(640, 480, P3D);
}

void setup() {
    pointCloud = new PointCloud(this, nbPoints);
    cam = new PeasyCam(this, 400);
    loadCloud();
    background(40);
}
void loadCloud(){
    int c = color(250);

    for(int i = 0; i < nbPoints; i++){
	float x = cos(i * millis() / 40000f);
	float y = cos(i * millis() / 62000f);
	float z = cos(i * millis() / 52000f);

	DepthPoint p = new DepthPoint(x * 100,
				      y * 100,
				      z * 100, c);
	pointCloud.addPoint(p);
    }
    pointCloud.loadVerticesToNative();
    colorMode(RGB, 255);
}
void draw() {
    loadCloud();
    pointCloud.drawSelf((PGraphicsOpenGL) g);
}
void keyPressed(){
    background(40);
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![Screenshot of the cloud.pde sketch](../.gitbook/assets/image%20%283%29.png)

#### Use case in Natar and PapARt 

In PapARt we extend this class to stream points as fast and efficiently as possible.  You can extend the PointCloud class to stream your own points. 

