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


### Installation Process

Below are the steps to install MAYA desktop:

> Go to [Maya download](https://www.autodesk.com/education/free-software/maya)

> Create an account using any educational email id

> Choose version, operation system and language

> Install the software and enter the licence key sent to the registered email

> MAYA desktop will be installed and ready to use


## Scripting in MAYA

> To start scripting in MAYA, first open file and crete a scene

> Next import any object and position it and scale it 

> Next go to create and create a circle and a plane

![Branching]("https://github.com/Sindhurakolli/DMDD_portfolio/blob/master/circle_and_plane.png")

> Now go to create and create a camera and a light. Position the light and camera with respect to object

<img src = "https://github.com/Sindhurakolli/DMDD_portfolio/blob/master/light_camera.png" width="600" height="600"/>

> Translate and Rotate the light and camera to point towards the object

> Select the camera and press SHIFT and then select the light and circle and press P to pair the camera, light and the circle and then select the circle

> Now click on Panels option and change perpective to camera which we created in the earlier step

<img src = "https://github.com/Sindhurakolli/DMDD_portfolio/blob/master/Changing_the_view.png" width="600" height="600"/>

> Make sure that the object looks as per the required dimensions

> Go to view option and add the required background 

<img src = "https://github.com/Sindhurakolli/DMDD_portfolio/blob/master/create_background.png" width="600" height="600"/>

> After creating the background, go to the image plane shape and assign material to the plane

<img src = "https://github.com/Sindhurakolli/DMDD_portfolio/blob/master/assign_material.png" width="600" height="600"/>


> Click on render view and Choose the appropriate render and set the type, quality and resolution of image using render      settings

> Open the script editor and run the script mentioned below

<img src = "https://github.com/Sindhurakolli/DMDD_portfolio/blob/master/code.png" width="600" height="600"/>


## The Image Generation Part


### Finalized Script to rotate and take images

```python
import maya.cmds
cmds.setAttr('defaultRenderGlobals.ren', 'mayaHardware2', type = 'string')
cmds.setAttr('defaultRenderGlobals.imageFormat', 32) 

cx = 0
i = 0
s = cmds.ls(selection = True)
camName = "camera1"
camPos = 0
obj = s[0]
deg = 45
cy = 0
cz = 0
def screenShot(i):
    mel.eval('renderWindowRender redoPreviousRender renderView')
    editor = 'renderView'
    cmds.renderWindowEditor(editor, e = True, refresh = True, writeImage = ('path' + str(i)))


while(cx<= 360):
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
            l = "_X_"+str(cx) + "_Y_"+str(cy) + "_Z_"+str(cz)
            camPos = cmds.xform(camName, q=True, ws=True, rp=True)
            if( camPos[1] > 1.0):
                screenShot(l)

            cz = cz + deg
        cy=cy+deg
    cx=cx+deg

```


* * *


[The Database Part](./another-page.html).


* * *





