---
layout: post
title: PDF AND IMAGE TOOLS
subtitle: A tool for converting between PDF to image and image formats.
categories: TOOLS
tags: [TOOLS, CODING]
---

## Introduction
The core function of the software is implemented based on [ImageMagick's Magick++](https://imagemagick.org/script/magick++.php), and the graphical interface is based on the [MFC framework](https://docs.microsoft.com/en-us/cpp/mfc/framework-mfc?view=msvc-170). Its main function is to achieve high-quality conversion between PDF to image and image formats.

#### This is an impromptu rough little program, the code is badly written, and the functions can only be used as needed.
< center class = "half">
<img src="https://raw.githubusercontent.com/Dot4diw/PDF-AND-IMAGE-TOOLS/main/BYCPLUSPLUS/PAIT/SourceFiles/PAIT-Screenshot.jpg" width = "50%" align = left> <img src = "https://raw.githubusercontent.com/Dot4diw/PDF-AND-IMAGE-TOOLS/main/BYCPLUSPLUS/PAIT/SourceFiles/Screenshot1.jpg" width = "50%" align = right>
</center>

## PDF Convert to Image
Input a PDF file, set the output resolution and format, click convert to convert PDF to image.

## Image format conversion
Support mutual conversion between various commonly used image formats.

## Installation guide
Step1. Download the installation package from [PDF-AND-IMAGE-TOOLS/BYCPLUSPLUS/PAIT/PAIT-Installer/PAIT-Installer.msi](https://github.com/Dot4diw/PDF-AND-IMAGE-TOOLS/blob/main/BYCPLUSPLUS/PAIT/PAIT-Installer/PAIT-Installer.msi) and install it.

Step2. Download ImageMagick installation package from [PDF-AND-IMAGE-TOOLS/BYCPLUSPLUS/PAIT/SourceFiles/ImageMagick-7.1.0-29-Q16-HDRI-x64-dll.exe](https://github.com/Dot4diw/PDF-AND-IMAGE-TOOLS/blob/main/BYCPLUSPLUS/PAIT/SourceFiles/ImageMagick-7.1.0-29-Q16-HDRI-x64-dll.exe) or https://imagemagick.org/script/download.php#windows and install it. Please check the "Add application directory to your system path" and "Install development headers and libraries for C and C++" options when installing.

![image](https://raw.githubusercontent.com/Dot4diw/PDF-AND-IMAGE-TOOLS/main/BYCPLUSPLUS/PAIT/SourceFiles/ImageMagick-Install-Guide.jpg)

Step3. Running.

### Note: 
#### 1). The path and output file name do not support Chinese, please enter the English path and the name.
#### 2). PDF to image only supports single page pdf.
.
