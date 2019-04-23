---
layout: default
---

**Content**

*   Introduction to MAYA

*   Installation Process

*   Scripting in MAYA

*   Database

*   Website

*   Cloud integration



## Introduction to MAYA

Autodesk Maya, commonly shortened to Maya, is a 3D computer graphics application that runs on Windows, macOS and Linux, originally developed by Alias Systems Corporation (formerly Alias|Wavefront) and currently owned and developed by Autodesk, Inc. It is used to create interactive 3D applications, including video games, animated film, TV series, or visual effects.
Maya 3D animation software offers a comprehensive creative feature set for 3D computer animation, modeling, simulation, rendering, and compositing on a highly extensible production platform. Maya has next-generation display technology, accelerated modeling workflows, and tools for handling complex data.


## Installation Process

Below are the steps to install MAYA desktop:

> Go to [Maya download](https://www.autodesk.com/education/free-software/maya)

> Create an account using any educational email id

> Choose version, operation system and language

> Install the software and enter the licence key sent to the registered email

> MAYA desktop will be installed and ready to use


## Scripting in MAYA

> To start scripting in MAYA, first open file and crete a scene

> Next import any object and position it and scale it 

> Next go to create and create a circle and a plane as below

![Branching](https://raw.githubusercontent.com/Sindhurakolli/DMDD_portfolio/master/circle_and_plane.png)

> Now go to create and create a camera and a light. Position the light and camera with respect to object

![Branching](https://raw.githubusercontent.com/Sindhurakolli/DMDD_portfolio/master/light_camera.png)

> Translate and Rotate the light and camera to point towards the object

> Select the camera and press SHIFT and then select the light and circle and press P to pair the camera, light and the circle and then select the circle

> Now click on Panels option and change perpective to camera which we created in the earlier step

![Branching](https://raw.githubusercontent.com/Sindhurakolli/DMDD_portfolio/master/Changing_the_view.png)

> Make sure that the object looks as per the required dimensions

> Go to view option and add the required background 

![Branching](https://raw.githubusercontent.com/Sindhurakolli/DMDD_portfolio/master/create_background.png)

> After creating the background, go to the image plane shape and assign material to the plane

![Branching](https://raw.githubusercontent.com/Sindhurakolli/DMDD_portfolio/master/assign_material.png)


> Click on render view and Choose the appropriate render and set the type, quality and resolution of image using render      settings

> Open the script editor and run the script mentioned below

![Branching](https://raw.githubusercontent.com/Sindhurakolli/DMDD_portfolio/master/code.png)

## The Image Generation Part


### Finalized Script to rotate and take images

```python

import maya.cmds as cmds
import maya.mel
s = cmds.ls(selection = True)
camName=cmds.listCameras()
cName='camera1'
cx=0
cy=0
cz=0
v=45
im=0
while (cx <=360):
   for a in s:
       x = a +"."+"rotate" +"X"
       cmds.setAttr(x,cx)

   cy=0
   while(cy<=360):
       for a in s:
           x = a +"."+"rotate" +"Y"
           cmds.setAttr(x,cy)

       cz=0
       while(cz<=360):
           for a in s:
               x = a +"."+"rotate" +"Z"
               cmds.setAttr(x,cz)
           cp=cmds.xform(cName,q=True,ws=True, rp=True)
           if(cp[1]>1):

               mel.eval('renderWindowRender redoPreviousRender renderView')
               editor =  'renderView'
               cmds.renderWindowEditor( editor, e=True,refresh = True, writeImage=('/Users/../images/object/object_name'+'_X'+str(cx)+'_Y'+str(cy)+'_Z'+str(cz)))
           im=im+1
           cz=cz+v
       cy=cy+v
   cx=cx+v

```

The above script is used to rotate the circle with camera and light around the object in all the three planes "X", "Y", "Z" with the interval of 45 degrees until 360 degrees and capture the screenshots of the images and store in the mentioned folder path.

This script creates 540 images per object when it is rotated in all axis.

All the images are stored in database which is described in the below link.


* * *


[The Database Part](./another-page.html).


* * *





