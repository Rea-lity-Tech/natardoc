---
description: SVG in Processing with Fonts and Images
---

# SVGExtended

### Description 

SVG support is quite limited in Processing. This library extends the possiblities: 

* Read images embedded in Base64. 
* Read images in links. 
* Display texts from SVG. The font support might not be perfect yet. 

### Download

{% embed url="https://github.com/Rea-lity-Tech/SVGExtended/releases/download/3.3.7.2/SVGExtended.tgz" caption="Click to download." %}

{% embed url="https://github.com/Rea-lity-Tech/SVGExtended" caption="GitHub project" %}

### Usage 

The library is used in PapARt and Natar to read markerboards \(list of markers in a SVG file\). The text support was added for [Soby](https://github.com/poqudrof/Soby) an experimental presentation software inspired by Sozi and Prezi. 

### Example

{% code title="LoadDisplaySVG.pde" %}
```java
import tech.lity.rea.svgextended.*;

PShape bot1, bot2;
void setup() {
  size(640, 660);
  // The file "bot1.svg" must be in the data folder

  // of the current sketch to load successfully
  bot1 = loadShape("bot2.svg");

  // The file "bot2.svg" must be located with "bot1.svg"
  bot2 = new PShapeSVGExtended(loadXML("bot2.svg"));
} 

void draw(){
  background(102);
  shape(bot1, 0, 0); 
  shape(bot2, 0, 320);
}
```
{% endcode %}

