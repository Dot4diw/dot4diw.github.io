---
layout: post
title: How to use the ImageMagick Magick++ API for development
subtitle: How to configure Magick++ in Visual Studio
categories: CODING
tags: [C++, CODING]
---

# How to use the ImageMagick Magick++ API for development.

## Introduction

Magick++ is the object-oriented C++ API to the [ImageMagick](http://www.imagemagick.org/) image-processing library, the most comprehensive open-source image processing package available.  [Magick++](https://imagemagick.org/script/magick++.php) provides a thread-safe object-oriented C++ interface to ImageMagick.  See [A Gentle Introduction to Magick++](https://imagemagick.org/Magick++/tutorial/Magick++_tutorial.pdf) for an introductory tutorial to Magick++. 

## How to configure Magick++ in [Visual Studio](https://visualstudio.microsoft.com/)

**Step1. Install the Magick++ delvelopment headers and libraries for C/C++/**

First, you need to download the installation package of [ImageMagick](https://download.imagemagick.org/ImageMagick/download/binaries/ImageMagick-7.1.0-30-Q16-HDRI-x64-dll.exe) of *Q16-HDRI-x64-dll.exe from ImageMagick's official website, and then double-click to install it. Note that you need to check the "Add application directory to your system path" and "Install development headers and libraries for C and C++" options during installation, as shown in the following figure.

![2022-04-22_083050](https://raw.githubusercontent.com/Dot4diw/dot4diw.github.io/main/imagesource/2022-04-22_083050.jpg)

**Step2. Configure the Magick++ development environment in Visual Studio**

First you need to install Visual Studio 2022 or other version. Then open Visual Studio and create a new Console Application project as shown below.

![2022-04-22_083710](https://raw.githubusercontent.com/Dot4diw/dot4diw.github.io/main/imagesource/2022-04-22_083710.jpg)

After that, open the project properties and configure it once in the order shown in the figure below.

![2022-04-22_084422](https://raw.githubusercontent.com/Dot4diw/dot4diw.github.io/main/imagesource/2022-04-22_084422.jpg)
![2022-04-22_084735](https://raw.githubusercontent.com/Dot4diw/dot4diw.github.io/main/imagesource/2022-04-22_084735.jpg)
![2022-04-22_084812](https://raw.githubusercontent.com/Dot4diw/dot4diw.github.io/main/imagesource/2022-04-22_084812.jpg)
![2022-04-22_084947](https://raw.githubusercontent.com/Dot4diw/dot4diw.github.io/main/imagesource/2022-04-22_084947.jpg)

**Step3. Write a sample program for Magick++ and run it.**

The following code is taken from the [Magick++ official website](https://imagemagick.org/script/magick++.php). Paste this code into Visual Studio and let it compile. If the compilation is successful, it means that the Magick++ development environment has been successfully configured.

```C++
// Code from https://imagemagick.org/script/magick++.php
#include <Magick++.h> 
#include <iostream> 

using namespace std;
using namespace Magick;

int main(int argc, char** argv)
{
    InitializeMagick(*argv);

    // Construct the image object. Seperating image construction from the 
    // the read operation ensures that a failure to read the image file 
    // doesn't render the image object useless. 
    Image image;
    try {
        // Read a file into image object 
        image.read("logo:");

        // Crop the image to specified size (width, height, xOffset, yOffset)
        image.crop(Geometry(100, 100, 100, 100));

        // Write the image to a file 
        image.write("logo.png");
    }
    catch (Exception& error_)
    {
        cout << "Caught exception: " << error_.what() << endl;
        return 1;
    }
    return 0;
}
```



![2022-04-22_085754](https://raw.githubusercontent.com/Dot4diw/dot4diw.github.io/main/imagesource/2022-04-22_085754.jpg)

**Step4. Enjoy it!**

