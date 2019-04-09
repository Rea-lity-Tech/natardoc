---
description: 'Skatolo is a GUI library for Processing, forked from ControlP5'
---

# Skatolo GUI for Ruby and AR

### Download

Skatolo is on [github](https://github.com/Rea-lity-Tech/Skatolo). You can get the latest realease here: [download](https://github.com/Rea-lity-Tech/Skatolo/releases/download/1.1.3/skatolo.tgz). 

### Why a fork ?

ControlP5 is an old but still maintained library. We wanted to develop new features for it such as multi-touch support and support in Ruby. Thes rework was first to understand better the code and update it to our coding standards.

{% hint style="success" %}
Please use the [original library](https://github.com/sojamo/controlp5) in your projects if you are not sure which one to use. It is easier to use for imports.
{% endhint %}

### Use cases

This library is for an **advanced** use of ControlP5 for multi-touch and specially for the PapARt and Natar libraries.

The second use is as GUI for [JRubyArt](https://github.com/ruby-processing/JRubyArt). We added some features to ControlP5 and a wrapper to make it interact nicely with our Ruby code. Here is an example:

{% code-tabs %}
{% code-tabs-item title="Slider.rb" %}
```ruby
require 'skatolo'
# In this simple sketch we attach a slider to skatolo in the regular way, with
# a named slider 'background_color' and thanks to some fancy metaprogramming
# we can read the result from background_color_value in the sketch
attr_reader :skatolo

def settings
  size(400, 300)
end

def setup
  sketch_title 'Skatolo Slider'
  create_gui
  skatolo.update # this step is important
end

def draw
  background(background_color_value)
end

def create_gui
  @skatolo = Skatolo.new(self)
  skatolo.add_slider('background_color')
         .set_position(10, 10)
         .set_size(150, 20)
         .set_range(80, 255)
         .set_value(180)
         .set_label('Background color')
 end

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### New widgets and features

* PixelSelect - Select a pixel in the screen.
* HoverButton and HoverToggle: Button and toggle without click. They are used in [PapARt examples](https://github.com/poqudrof/Papart-examples/tree/unstable/first-examples/ProCamDepth/Gui).
* HoverKnob: Know without click.
* OffScreen buttons: [example](https://github.com/poqudrof/Skatolo/blob/master/examples/advanced/offscreen/offscreen.pde).
* Multi-touch : [example](https://github.com/Rea-lity-Tech/Skatolo/blob/master/examples/advanced/multitouch/multitouch.pde).

## Distribution 

#### Source

Github: [https://github.com/Rea-lity-Tech/Skatolo](https://github.com/Rea-lity-Tech/Skatolo)

#### Processing

You can get the latest realease here: [download](https://github.com/Rea-lity-Tech/Skatolo/releases/download/1.1.3/skatolo.tgz). 

#### Ruby gem

`gem install skatolo`

#### Maven

{% code-tabs %}
{% code-tabs-item title="pom.xml" %}
```markup
<dependency>
   <groupId>tech.lity.rea</groupId>
   <artifactId>skatolo</artifactId>
   <version>1.1</version>
</dependency>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

