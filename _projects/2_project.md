---
layout: page
title: Automatic review of reports
description: Deep Learning, Object Detection, LabelImg 
img: /assets/img/DSC-ENTEL/project_image.jpg
importance: 2
category: code
---

## Objective

The [challenge](https://www.kaggle.com/c/datathon-entel-2021-reto1/data) involves developing an object detection and OCR model to automate the review of documents that a technician collects during each telecommunication antenna installation and that are then manually reviewed when they are delivered to their base, which could lead to human error.
    
## Description

For this challenge we are only asked to determine the location of 3 fields of the format (2 signatures and 1 date) and to obtain the handwritten date separated in day month and year.

<p align="center">
    <img src="/assets/img/DSC-ENTEL/data_locations.jpeg" style="max-width: 100%" 
     width="300" height="400"/>
</p>


## Solution

Our solution is "**totally free**" and not depending of any api's that might involucrate a cost in the near future. It is divided into 3 main parts:
+ First, we label the dates presented in the documents in order to apply supervised object detection on numbers. We used the free available software [LabelImg](https://github.com/tzutalin/labelImg)

<p align="center">
    <img src="/assets/img/DSC-ENTEL/labeling.gif" style="max-width: 100%"
     width="600" height="300"/>
</p>

+ Second, we developed an image preprocessing module, which consists in image aligment, standarization of orientation, size, proportion and extraction of sub-images (sign, date)
<p align="center">
    <img src="/assets/img/DSC-ENTEL/preprocessing.png" style="max-width: 100%"
     width="600"/>
</p>
+ Third, we developed a deep learning module that consists in:
    - A fine-tuned CNN (DenseNet) for sign presence classification
    - A FasterRCNN architecture for detecting and extracting the numbers and separators that appear on date
         
<p align="center">
    <img src="/assets/img/DSC-ENTEL/application.gif" style="max-width: 100%"
     width="600"/>
</p>
## Code
See the solution and code in the github [repository](https://github.com/williamberrios/Datathon-Entel-Object-Detection)