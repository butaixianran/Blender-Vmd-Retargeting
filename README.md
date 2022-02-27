### Notice: If you already bought it, make sure you update it to ver1.1.4, which fixed some important bugs   


# Language
[中文](Readme.cn.md)  
[日本語](Readme.jp.md)

# Blender Addon: Vmd Retargeting
This blender addon will import motion from mmd's .vmd file onto Daz or CC3 models, with or without mmd model.  

![basic](img/addon_screen_basic.jpg) 
![full](img/addon_screen_ful.jpg)

# Demo Video
[https://youtu.be/Xgfu8oSjUUs](https://youtu.be/Xgfu8oSjUUs)  
[![](img/FeaturedImages01_half.jpg)](https://youtu.be/Xgfu8oSjUUs)  

# Info
### Download
[https://blendermarket.com/products/vmd-retargeting](https://blendermarket.com/products/vmd-retargeting)

### Blender Forum
[https://blenderartists.org/t/addon-retarget-mmds-vmd-motion-to-daz-or-cc3/1361902](https://blenderartists.org/t/addon-retarget-mmds-vmd-motion-to-daz-or-cc3/1361902)


### Github
This github repo is for issues and translation.  
[https://github.com/butaixianran/Blender-Vmd-Retargeting](https://github.com/butaixianran/Blender-Vmd-Retargeting)

### Version
Addon: 1.2.0
Blender: 3.0

# Feature
* Import motion from vmd file without a mmd model
* Or retarget body motion from a mmd model.
* 
* Import body, eyeball, facial, viseme and camera motion separately
* Ignore feet rotation when Daz/CC3 character is on high heel.
* Set interpolation and easing as you wish
* Set arm rotation rate, to prevent hands poke into chest.  
* Set camera height offset or rotation rate if needed  

# Install
* Install the .zip file you get from online shop.  
* Search "Vmd retargeting" in your addon list and enable it
* In viewport, press "N" to display tool panels, select "Vmd Retarget" panel  

If you are new to blender and don't know how to install a blender addon, search: "blender install addon" in google.  

# How to use
## Prepare a character
This addon supports:
* Daz Genesis 8 imported by [diffeomorphic daz importer addon](https://diffeomorphic.blogspot.com/) 
* CC3(Character Creator) model imported by [cc3 blender tools addon](https://github.com/soupday/cc3_blender_tools)  

For characters imported by fbx, cc3 model should work too. But for daz model, retargeting facial and viseme motion won't work.  

If you wanna use a Daz model imported by fbx, tell use why. If it is reasonable, we'll add it.  

### Prepare CC3 model
**No preparing is needed.**   
But do not export your character from iClone. We only tested by exporting from Character Creator.  

When exporting, make sure you choose A-Pose.(Need CC3+)  
![](img/cc3_export_setting.jpg)    
The key is, after importing into Blender, its pose should be like this:    
![](img/cc3_def.jpg)  


### Prepare Daz model
Diffeomorphic daz importer is complex. But we just need click a few buttons to get it done.  

You need to know the basic of how to setup and export a daz model for Diffeomorphic daz importer.
Check its official tutorial for that.  

And when importing model to blender, you need 3 things:
* Merge all armatures into body's armature
* Face Unit morph and Viseme morph
* Make all bones poseable.  

**The easiest way for these, is importing a character by click "Easy Import Daz" button.**  
By default, it already checked Merge Rigs for you.  
So, you just need to check "Face Units" and "Visemes", then import.  

After importing, go to "**Finish**" section of Diffeomorphic daz importer's panel. Click "**Make All Bones Poseable**"

Now, your daz model is prepared.

## Prepare a vmd file
No preparing is needed in most cases.

But, there are some old or weird vmd files don't use normal bone names or file structure.  

If you imported a vmd file like this onto Daz or CC3, your model gonna jump from one pose to another, like a robot dance.  

For those vmd files, just open MikuMikuDance, load a TDA model, and load this vmd file on it, then re-export it as a new vmd file.  

This new vmd file will work.

## Import vmd
It is pretty simple:
* Select your character's armature
* Select a vmd file
* Select your model type (CC3 or Daz)
* Check which part you'd like to import
* **Make sure** your active armature is your Daz or CC3 model, click "Execute", done.

Each part will be an action wrapped into a strip on a track, in NLA (Nonlinear Animation).  
So, it won't mess up your timeline, and you can move or delete them like clips.


## Options
Move your mouse onto those operators (button, checkbox or list), will display a useful tooltip.  

High Heel Tooltip:  
![tooltip_high_heel](img/tooltip_high_heel.jpg)  

Camera Height Offset Tooltip:  
![tooltip_height_offset](img/tooltip_height_offset.jpg)  

### High Heel
check to ignore rotation on feet.  

### Body Motion
#### Tracks
Body motion is separated into mutiple tracks.  

For example, mmd doesn't have motion layers, so they use mutiple bones which does the same thing, to simulate motion layers. And we handle that by adding this bone's motion into a real new layer.

For now, we only do this for: center and groove bone's location.  

#### IK
**If a vmd motion does not use IK, just uncheck it**.   

**IK works fine in most cases. But if leg rotates widely, then you need to know following information:**  

CC3 and Daz model don't have IK by default. So this addon creates IK for legs when importing body motion from vmd file.  

But a problem with Daz/CC3 model is: there is no bending on their knees' rest pose. In that case, IK will come with a IK Pole Bone, to tell knee which direction to point when bending.  

So, Daz/CC3's knees are always pointing to IK Pole bones in front of them. And IK Pole Bones are following rotation of pelvis bone.  

That works fine in most cases. But, if legs rotate too much, then IK Pole bones won't work well since they just following pelvis bone.  

So, in that case, you need to retarget motion from a mmd model. Since mmd model already has the motion on it, your Daz/CC3 model can get legs' final rotation without IK bone.  

Check the section: **Pick a mmd model as Source**

#### Arm rotation rate
Daz/CC3 has different arm length with mmd model. So, if mmd model puts hands on chest, they always poke into body when on Daz/CC3 model.

Set upperarm and forearm rotation rate to 0.8 will fix that in most cases. (Now this is default) 

#### Pick a mmd model as Source
If you picked a mmd model, addon will ignore body motion from vmd file and retarget body motion from your picked mmd model.  

Eyeball and morph motion are still loaded from vmd file.  

You need blender mmd tools to import a mmd model into blender:  
[https://github.com/UuuNyaa/blender_mmd_tools](https://github.com/UuuNyaa/blender_mmd_tools)  

**When importing a mmd model, uncheck rename bones!** We use its japanese bone name to map bones.    
![](img/uncheck_rename_bones.jpg)  

After importing mmd model, then import your vmd motion onto this mmd model **by using mmd tools, not this addon!**   

Which is: select your mmd model, go to `File menu->Import->Vmd file`, and select a vmd file.  
Now, your mmd model should has a motion on it.   

Then select your Daz or CC3 model, use the pick tool of "Source" from this addon's panel, **pick the armature of your mmd model. Not the empty parent!**    
![](img/mmd_armature.jpg)  

**Make sure you select your Daz or CC3 model**, then click "Execute".    

It will retargeting every frame of evey mapping bone's final rotation from mmd model, not just key frames, so it will be very slow.   

And it doesn't need an IK bone on Daz/CC3 model.  

**There is a video tutorial for this:**   
[https://youtu.be/rttA3v_5S2I](https://youtu.be/rttA3v_5S2I)  
[![](img/convert_motion_from_mmd_model_to_daz_tutorial-resiez.jpg)](https://youtu.be/rttA3v_5S2I)  

### Eyeball/Facial/Viseme
CC3 doesn't come with viseme morphs, it's a feature for iClone. So, this addon uses facial expression morphs to simulate viseme. It is ok, but won't as good as real viseme morphs, and it won't move teeth.  

### Interpolation/Easing:
You can find examples from [https://easings.net/](https://easings.net/)  

![](img/easing.jpg)  

If your model's motion is not smooth, you can try set interpolation to "Linear". In some cases, linear is pretty smooth.  

This setting won't affect camera motion. Camera motion is always linear.  

### Camera Rate/ Height Offset
Daz/CC3 model has different model size with mmd model. So, camera motion need to be adjusted.  

Default value works fine for almost every case. 
But if your model is a CC3 character with high heel, you need to move camera up with 8cm.  


### Debug mode
Debug mode will print down everything in console log. It gonna slow down the retargeting a lot.  

So only check it when importing a vmd file with a single pose.


# Limits
## Shoulder Rotation
There are 3 shoulder bones on a mmd model: shoulder, shoulder P, shoulder C. This addon ignored shoulder P and shoulder C.  

## Twist Bone
MMD model also comes with twist bones. They are used only in a few vmd files. They are not handled when importing with vmd file.  

So, for these kind of vmd motion, you need retarget body motion from a mmd model.  

## Prop motion
This addon won't handle that.


# Update Log:
* Set Arm rotation rate to 0.8 as default, since every vmd motion put hands to chest.
* Add shoulder rotation rate then remove it, seems not very useful.
* Add IK checkbox, uncheck to not create IK bones.
* Handle rotation for center bone
* Remove leg's rotation when importing from vmd file since IK takes control
* Fix feet rotation when retargeting from mmd model
* Arm rotation rate now works when retargeting motion from a mmd model
    - This is done by using a new way to convert mmd model's upper body motion
* When executing with a wrong model type, now shows a message.