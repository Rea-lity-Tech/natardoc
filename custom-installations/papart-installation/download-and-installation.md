# Download and installation

## Step 1: Install Processing, and the required libraries.

#### Processing

{% hint style="info" %}
Skip this step if Processing is already installed in your system.
{% endhint %}

You need first to install [Processing](https://processing.org/download/) for you system. Once it is installed you need to run it once so that it creates all the folders.

#### Libraries from Processing library list

You will need the **Video library**, and for some examples sound, they are available through Processing: `Sketch -> Import Library -> Add a Library` or directly [here](https://github.com/processing/processing-video/releases/download/latest/video.zip).

#### The PapARt library and its dependencies

All these libraries must be installed in your `$sketchbook/libraries/` folder. 

{% hint style="warning" %}
The libary folder is different from one operating system to another.

* Linux: `/home/toto/sketchbook/libraries`. 
* OSX: `/Documents/Processing/libraries`. 
* Windows: `/My Documents/Processing/libraries`.
{% endhint %}

Download the [PapARt examples](https://github.com/poqudrof/Papart-examples/archive/master.zip), and extract them in your `$sketchbook` folder.

1. Then download and install the [PapARt library](http://dist.rea.lity.tech/papart/PapARt-1.2.tgz).
2. PapARt requires additonal libraries here is the collection: [link](http://dist.rea.lity.tech/libs/bundles/libraries.zip). It is used for math, network, 3D, and GUI. It includes well known Processing libraries: PeasyCam, OSCP5, Video, Toxiclibs. And custom ones: SVGExtended, ProcessingTUIO, Skatolo, GuiModes, and Reflections.

#### OpenCV native dependency: JavaCV

The last library is JavaCV, it embeds OpenCV \(C++\) pre-compiled. Consequenly you need to download the right package for your platform:

* [All architectures](http://dist.rea.lity.tech/libs/javacv/javacv.zip) \(larger\)
* Windows 64 bits: please use all architecture for now.
* [Linux x86\_64](http://dist.rea.lity.tech/libs/javacv/javacv-linux-x86_64.tgz). 
* [Mac OSX](http://dist.rea.lity.tech/libs/javacv/javacv-macosx-x86_64.tgz): tests required, use all architecture.
* Experimental: [armhf / Raspberry pi](http://jiii.fr/papart/libraries/javacv-linux-armhf.tgz), [android](http://jiii.fr/papart/libraries/javacv-android-arm.tgz). Use all architecture if you have doubts.

{% hint style="danger" %}
You need to restart processing after installing a new library or adding sketches in your sketchbook.
{% endhint %}

#### Check your installation

Start Processing, then go to menu `File -> Examples`. Then in the pop-up, expand the folder `Contributed libraries`. You should see most of the installed libraries: `PeasyCam`, `PapARt`, `Toxiclibs`, `SVGExtended` etc... If not check that you installed the libraries correcty. You can follow this official [guide to install libraries](https://github.com/processing/processing/wiki/How-to-Install-a-Contributed-Library).

