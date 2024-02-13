#### This addon handles most vmd motion very well. If you can not make it work, view "[Common Issue](#Common-Issue)" part for solution.   


# Language
[中文](Readme.cn.md)  

# Blender Addon: Vmd Retargeting
This blender addon will import motion from mmd's .vmd file onto Daz or CC models, with or without mmd model.  

![basic](img/addon_screen_basic.jpg) 
![full](img/addon_screen_ful.jpg)

# Demo Video
[https://youtu.be/Xgfu8oSjUUs](https://youtu.be/Xgfu8oSjUUs)  
[![](img/FeaturedImages01_half.jpg)](https://youtu.be/Xgfu8oSjUUs)  

# Tutorial Video
## How to use this addon
[https://youtu.be/li7yjJKbbgI](https://youtu.be/li7yjJKbbgI)  

## Blender tutorial
Daz Hair and cloth physics in Blender: [https://youtu.be/1RzwmTgcfys](https://youtu.be/1RzwmTgcfys)  
Export mmd motion to Daz Studio: [https://youtu.be/FEA9hVouKFg](https://youtu.be/FEA9hVouKFg)  

[Daz Studio Setting for Importing Motion](#daz-studio-setting-for-importing-motion)[Not Mentioned In Above Video]

# Bonus
## Conver Daz Model to MMD
Check its own readme page: [Daz to MMD](daz_to_mmd.md)   

## Create Proxy Mesh For Realtime Physics
Check section: [Proxy Mesh For Realtime Physics](#Proxy-Mesh-For-Realtime-Physics)  

# Info
### Download
[https://blendermarket.com/products/vmd-retargeting](https://blendermarket.com/products/vmd-retargeting)

### Blender Forum
[https://blenderartists.org/t/addon-retarget-mmds-vmd-motion-to-daz-or-cc3/1361902](https://blenderartists.org/t/addon-retarget-mmds-vmd-motion-to-daz-or-cc3/1361902)


### Github
This github repo is for issues and translation.  
[https://github.com/butaixianran/Blender-Vmd-Retargeting](https://github.com/butaixianran/Blender-Vmd-Retargeting)

### Version
Addon: 1.24.0     
Blender: 3.0 or later  

# Feature
* Import motion from vmd file without a mmd model
* Or retarget body motion from a mmd model.
* 
* Import body, eyeball, facial, viseme and camera motion separately
* Ignore feet rotation when Daz/CC character is on high heel.
* Set interpolation and easing as you wish
* Set arm rotation rate, to prevent hands poke into chest.  
* Set camera height offset or rotation rate if needed  
* 
* (**Bonus**) [Convert Daz model to MMD](daz_to_mmd.md)

# Install
* Install the .zip file you get from online shop.  
* Search "Vmd retargeting" in your addon list and enable it
* In viewport, press "N" to display tool panels, select "Vmd Retarget" panel  

If you are new to blender and don't know how to install a blender addon, search: "blender install addon" in google.  

# How to use
## Prepare a character
This addon supports:
* Daz Genesis 8 imported by [diffeomorphic daz importer](https://bitbucket.org/Diffeomorphic/import_daz/wiki/Home)
* Daz Genesis 8 imported by [Daz to Blender Bridge for blender 3.x](https://github.com/butaixianran/DazToBlender)  
* Daz Genesis 8 imported by [Official Daz to Blender Bridge 2022](https://www.daz3d.com/forums/discussion/572806/official-daztoblender-bridge-2022-what-s-new-and-how-to-use-it)  
* CC4(Character Creator) imported by [cc blender tools addon](https://github.com/soupday/cc_blender_tools)  

![model type](img/addon_model_type.jpg)  

For characters imported by fbx, cc4 model works too. But for daz model, facial and viseme motion won't work.  

### For Blender 4.x
To make addon "**diffeomorphic daz importer**" work with Blend 4.x, you need download its latest Development version. The stable version on dropbox only works for Blender 3.x.   
[https://bitbucket.org/Diffeomorphic/import_daz/wiki/Home](https://bitbucket.org/Diffeomorphic/import_daz/wiki/Home)  

![](img/download_diff_daz_importer_source_code.jpg)  

Then unzip the downloaded file, its folder name should be something like "Diffeomorphic-import_daz-xxxxxxxxxx".   
![](img/diff_daz_importer_rename.jpg)  


Rename this folder to "import_daz", zip it into a new `.zip` file. Install this new zip file as Blender addon.  

Now, you have the latest **diffeomorphic daz importer** which works for Blender 4.x.  

### Prepare CC4 model
**No preparing is needed.**   
Just export it from Character Creator, not from iClone, and Mesh only, no animation.  

For CC4, when exporting, choose A-Pose  
![](img/cc3_export_setting.jpg)    

For CC4, After importing into Blender, its pose should be like this:    
![](img/cc3_def.jpg)  


### Prepare Daz model(with Diffeomorphic Daz Importer)
[Diffeomorphic daz importer](https://diffeomorphic.blogspot.com/) is complex. But we just need click a few buttons to get it done.  

You need to know the basic of how to setup and export a daz model for Diffeomorphic daz importer.
Check its official tutorial for that.  

When importing model to blender, you need 3 things:
* Merge all armatures into body's armature
* Facial morph and Viseme morph
* Make all bones poseable.  

**The easiest way for these, is importing a character by clicking "Easy Import Daz" button.**  

#### For Genesis 8
**Click "Easy Import Daz" button, not the "Import Daz" button**  
**Click "Easy Import Daz" button, not the "Import Daz" button**  

by default, it already checked "**Merge Rigs**" and "**Make All Bones poseable**" for you. If not, check them.  
Then, you just need to check "**Face Units**" and "**Visemes**", then import.  

Now, your daz model is prepared.  

#### For Genesis 9
You need diff daz importer **version 1.6.2+** to import a Daz Genesis 9 character.   

If you already has diff daz importer ver1.6.1 in your Blender, you have to remove it and re-open Blender, before installing version 1.6.2. Then re-config the Global setting after installing version 1.6.2. A lot of files and settings are changed.    

Click "Easy Import Daz" button. By default, it already checked "Merge Rigs" and "Make All Bones Poseable" for you.  
So, you just need to check "FACS", then import.  

Now, your daz model is prepared.  

**Be noticed, Genesis 9's twist bones are no longer in arms. Which makes MMD's twist bones can not map into Genesis 9's arm. So, any vmd motion uses twist bones, can not be converted to Genesis 9.**  





### Prepare Daz model (with Daz to Blender Bridge(DTB) for Blender 3.x)
This is for those who know how to use DTB. If you are not familiar with Daz or Blender, just choose the "**Diffeomorphic Daz Importer**" way.  

This one, is not the Official DTB 2022. It is a version updated by me, which works on Blender 3.x, fixed most issues in the Official DTB, and added a lot of useful options.  
[https://github.com/butaixianran/DazToBlender](https://github.com/butaixianran/DazToBlender)  

The best part of this one is, morph is on body mesh's shape key without driver. Also, there is no complex shader in materials, only standard Principled shader.   

**So, with this one, you can export Daz model with motion and materials from Blender to any other 3D tools, including game engine.**  

**After you installed DTB:**   
* In Daz, when exporting your model, check "**Include Morphs**"
* Go to "**choose morphs**" dialog window, click **Genesis 8 Facial Morphs** and **Visemes** Buttons on the left to add those morphs into export list.  
* Export.  
* In Blender, on DTB's panel, click import, Done.


### Prepare Daz model (with Official Daz to Blender Bridge(DTB) 2022)
Official DTB 2022 is released, with many old bugs and problems in it, never fixed. So, we really recommend you do not use this addon for now.  

For now, the only good part for Official DTB 2022 is, it is very easy to install. But it is not as good as the other 2 choices.    

You can learn it here about how to install or use it:  
[https://www.daz3d.com/forums/discussion/572806/official-daztoblender-bridge-2022-what-s-new-and-how-to-use-it](https://www.daz3d.com/forums/discussion/572806/official-daztoblender-bridge-2022-what-s-new-and-how-to-use-it)  

**After you installed DTB 2022:**   
* In Daz, when exporting your model, check "**Export Morphs**"
* Go to "**choose morphs**" dialog window, From "Pose Controls" category, add **Eyes**, **Mouth**, **Brow**  and **Visemes** morphs to the "**Morphs to Export**" list.  
* Export.  
* In Blender, on DTB's panel, click import, Done.  


## Prepare a vmd file
**No preparing is needed in most cases.**  

But, there are some very old vmd files don't use normal vmd file structure.  

If you imported a vmd file like this onto Daz or CC, your model gonna jump from one pose to another, like a robot dance.  

For those vmd files, just open MikuMikuDance, load a TDA model, and load this vmd file on it, then re-export it as a new vmd file.  

This new vmd file will work.  


## Import vmd
It is pretty simple:
* Select your character's armature
* Select a vmd file
* **Select model type**
* Check which part you'd like to import
* If this vmd motion doesn't use IK, then uncheck IK
* **Make sure** selected object is Daz or CC model, click "Execute", done.

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

For now, we only do this for: center and groove bone.  


#### Arm rotation rate
Daz/CC has different arm length with mmd model. So, if mmd model puts hands on chest, they always poke into body when on Daz/CC model.

Set upperarm and forearm rotation rate to 0.8 will fix that in most cases.  

But if you are using CC model, you better set it back to 1.0.   

### Arm rotation Euler plus
Works on forearms only. Use this with **Arm rotation rate** together to deal with hand poking issue.  
Default value:   
>Upperarm rotation rate: 0.9   
>Forearm rotation rate: 1.0   
>Forearm left: -5, 0, 3   
>Forearm right: -5, 0, -3   

If forearm pokes into body with default value, try those values:
>Upperarm rotation rate: 1.0   
>Forearm rotation rate: 1.0   
>Forearm left: 0, 0, 0   
>Forearm right: 0, 0, 0   

Or following values:  
>Upperarm rotation rate: 0.8   
>Forearm rotation rate: 0.8   
>Forearm left: -15, 0, 9   
>Forearm right: -15, 0, -9   


#### Pick_A_MMD_Model_As_Source
If you picked a mmd model, addon will ignore body motion from vmd file and retarget body motion from your picked mmd model.  

**Eyeball and morph motion are still loaded from vmd file. So you need to pick the same vmd file on addon, if you want to import eyeball and morph motion.**    

You need blender mmd tools to import a mmd model into blender:  
[https://github.com/UuuNyaa/blender_mmd_tools](https://github.com/UuuNyaa/blender_mmd_tools)  

**When importing a mmd model, uncheck rename bones!** We use its japanese bone name to map bones.    
![](img/uncheck_rename_bones.jpg)  

After importing mmd model, also import your vmd motion onto this mmd model **by using mmd tools, not this addon!**   

Which is: select your mmd model, go to `File menu->Import->Vmd file`, and select a vmd file.  
Now, your mmd model should has a motion on it.   

Then select your Daz or CC model, use the pick tool of "Source" from this addon's panel, **pick the armature of your mmd model. Not the empty parent!**    
![](img/mmd_armature.jpg)  

**Make sure you select your Daz or CC model**, then click "Execute".    

It will retargeting every frame of evey mapping bone's final rotation from mmd model, not just key frames, so it will be very slow.   

In this way, addon won't create IK bones on Daz/CC model.  

**Also, Arm Rotation rate and Arm rotation Euler plus won't work when using a MMD model as motion source.**  



**There is a video tutorial for this:**   
[https://youtu.be/rttA3v_5S2I](https://youtu.be/rttA3v_5S2I)  
[![](img/convert_motion_from_mmd_model_to_daz_tutorial-resiez.jpg)](https://youtu.be/rttA3v_5S2I)  

### Interpolation/Easing:
You can find examples from [https://easings.net/](https://easings.net/)  

![](img/easing.jpg)  

This setting won't affect camera motion. Camera motion is always linear.  

With default options, this addon will convert each vmd keyframe's interpolation into a blender's most similar build-in interpolation. This works fine for most cases but not all cases. 

If you want your motion on Daz/CC is the exactly as smooth as on a mmd model, there are 2 choices:  
* You can pick a mmd model as source on this addon, so it will convert every frame, not just keyframes
* Or, you can download [MikuMikuMoving](https://sites.google.com/site/mikumikumovingeng/), load mmd model and vmd motion into MikuMikuMoving, then export motion into a new vmd motion file. And when exporting, check "**Integrate layer**". So it will save every frame, not just keyframe. Then use that new vmd file with this addon. 


### Camera Rate/ Height Offset
Daz/CC model has different model size with mmd model. So, camera motion need to be adjusted.  

Default value works fine for almost every case. 
But if your model is a CC character with high heel, you need to move camera up with 8cm.  

# Limits
## Mother_Bone
On a mmd model, there is a bone called "全ての親", which means mother bone in English. A vmd motion should never uses this bone. It is designed for final user adjusts model's position after loading a vmd motion. In Blender, it is just like moving the whole object, not a bone.  

Since no vmd motion should use it, this mother bone is not handled in this addon.  

But, there is a few vmd motion creators ignore this rule. They just uses mother bone as another hip bone. Which makes it into an issue in mmd world.   

So, in mmd world, there is a free tool, to convert mother bone's motion into body bones, called "Motion Supporter" tool. If you have a vmd motion uses mother bone, you need to use this tool, do the conversion, then uses the converted motion with this addon.  

**MotionSupporter's How To**  
* Download: [https://bowlroll.net/file/233713](https://bowlroll.net/file/233713)  
* Unzip and run, select "**全親移植**" Section:  
![](img/motionSupporter_motherBone.jpg)  

* Line 1, select or drag vmd file into it.
* Line 2, select or drag mmd model file into it.

>**If a TDA model does not work well, uses a YYB Miku model. This tool's developer uses YYB Miku Model for testing.**   
>
>Download YYB Miku model：[https://bowlroll.net/file/284016](https://bowlroll.net/file/284016)  

* Line 3, location for converted vmd file.

* Line 4, **Do not check anything**.    

* Click the big button at bottom, to start converting.
* After converting, import this new vmd file with VMD Retargeting addon, Done.  


## Shoulder Rotation
There are 3 shoulder bones on a mmd model: shoulder, shoulder P, shoulder C. This addon ignored shoulder P and shoulder C.  


## Twist Bone
MMD model also comes with twist bones, only a few vmd motions use them. With Daz Model, this can be converted nicely. But CC model's twist bones work in a different way and won't be converted well.   

So, if you are using a vmd file come with motion on twist bones, you better use Daz model.  

So far as I know, there are only 2 vmd motion creators use twist bones. They are: Natsumi San and Fairy Tale.   

## Prop motion
This addon won't handle that.

# Proxy Mesh For Realtime Physics
## Video tutorial
Youtube:  
[https://youtu.be/lGAWgWxJjFc](https://youtu.be/lGAWgWxJjFc)  

## Create Proxy Mesh
On **this addon's Tool Panel**, there are 2 buttons: **Create and Clear Proxy Mesh**. They are useful for physics.  

Daz or CC model and their clothes have too many faces for collision. So, cloth physics gonna be very very slow.  

To make it faster, normally, you need do following manually:  
* copy body and clothes mesh
* add and apply decimate to those copied meshes

Then add cloth and collision to those decimated meshes. So you can have physics on those decimated meshes, which is much faster.  

Those decimated meshes for physics, are proxy meshes.  

With this addon, select a mesh, then "**Create Proxy Mesh**" button can create a decimated copy for this mesh.    
So, you just add cloth or collision to this proxy mesh and hide the original mesh, your cloth physics gonna be very fast.  

Following are full steps for this:  

**For body mesh:**  
* Select character's body mesh
* Click "**Create Proxy Mesh**" button
* Go to blender's physics panel, add "**Collision**" to this new proxy mesh.  
* In Collision's setting, modify "**thickness outer**" to 0.002
* Hide this proxy mesh, unhide original body mesh. (For both render and view window)
* Done.


**For cloth mesh which need physics:**  
* Set body's collision as above
* Select this cloth mesh
* Make sure it has a vertex group for pin.  
If you are using Daz's dforce clothes imported with Diff daz importer, this cloth will have a vertex group called "**dForce Pin**". So you don't need to create a vertex group by yourself.  

* Click "**Create Proxy Mesh**" button
* Go to blender's physics panel, add "**Cloth**" to this new proxy mesh.  
* In Cloth's setting, "**Shape**" section, "**Pin Group**" option, select your vertex group for pin. For Daz's dforce cloth, it gonna be "**dForce Pin**".
* Modify "**Simulation end**" frame at Cache section to your project's end frame.
* Click Bake

## Clear Proxy Meshes
Click this button on addon's Tool panel, will remove all created proxy meshes.  

## Arms poke into clothes
A common issue of physics is arms poke into dress or skirt then drag that dress or skirt away from lower body and broke it.  

You can not solve this without a proxy mesh. But with a proxy body mesh created by this addon, you can just remove both arms from the proxy body mesh, then hide it and render your image with original body mesh.  

Full step as following:
* Hide original body mesh, show and select body's proxy mesh.
* Go to edit mode
* Click on empty area to unselect all.
* Turn on view window's X-Ray mode.
* Select both arms' vertices
* Press "x", from pop-up menu, select "**vertices**" to remove arms. 
* Go back to object mode.
* Tunr off view window's X-Ray mode.
* Hide this body proxy mesh, show original body mesh.  

Now you can bake your cloth's physics.  


# Common Issue
We made a video for some common issues, check it out:  
[https://youtu.be/qBivoDgFpc4](https://youtu.be/qBivoDgFpc4)    

## Daz Genesis 9
You need diff daz importer **version 1.6.2+** to import a Daz Genesis 9 character.  

If you already has diff daz importer ver 1.6.1 in your Blender, you have to remove it and re-open Blender, before installing version 1.6.2. Then re-config the Global setting after installing version 1.6.2. A lot of files and settings are changed.  

Be noticed, Genesis 9's twist bones are no longer in arms. Which makes MMD's twist bones can not map into Genesis 9's arm. So, any vmd motion uses twist bones, can not be converted to Genesis 9.  

Also, Genesis 9 can not be converted to MMD model.  

## Leg won't bend
This vmd motion does not use IK.  

#### Solution 1
At addon panel, set IK to Off before importing.  

If feet are slipping after unchecked IK, set Position Rate X to 0.5.  

#### Solution 2
Another solution is, use a tool "**mmd MotionSupporter**"(Japanese language Only), convert FK into IK.  
* The good part of this is: after converting, there is almost no slipping on legs. 
* The bad part is: It need about 5 minutes to convert a vmd motion.

**MotionSupporter's How To**  
* Download: [https://bowlroll.net/file/233713](https://bowlroll.net/file/233713)  
* Unzip and run, select "**足FKtoIK**" Section:  
![](img/motionSupporter_FKtoIK.jpg)  

* Line 1, select or drag vmd file into it.
* Line 2, select or drag mmd model file into it.

>**Try not use a TDA model, YYB Miku model is much better.** With TDA model, after converting, new vmd motion could make your model's legs keep shaking.  
>
>Download YYB Miku model：[https://bowlroll.net/file/284016](https://bowlroll.net/file/284016)  

* Line 3, location for converted vmd file.

* Line 4, **Check options as screenshot**, otherwise, converted vmd motion, gonna make your model's legs keep shaking.  

>"足IKブレ固定" must be 0. It gonna set a distance range. In this range, legs gonna be treated as no movement. So, if this value>0, it gonna drop a lot of keyframes, which makes your model's legs keep shaking.  

* Click the big button at bottom, to start converting.
* After converting, import this new vmd file with VMD Retargeting addon, Done.  

## Arm rotation angle is different
Try arm rotation rate 1.0. Default is 0.9, to prevent poking.  

For CC character, just set all arm rotation to 1.0.  

## Character can not turn around, some motions are wrong
* At Diff Daz Importer addon's panel, in "**Global Setting**" dialog window, **Rigging** section, make sure you unchecked every option there. They gonna limit your model's rotation.   
![](img/rigging.jpg)  


## Body motion is totally wrong
This addon now is stable and handles most vmd motion very well. So, check following checklist to fix your issue quickly.  

* For CC character, make sure you export it from CC, with A-Pose, not from iClone
* For CC character, make sure you change model type to "CC3" or "CC4" on addon panel
* Make sure Blender version is 3.0+
* Make sure your addon is latest version
* Make sure Daz model is Genesis 8
* In Daz, make sure using "**Export to Bender**" menu to export "`.dbz`" file before importing to blender.
* When using "**Export to Bender**", have you clicked "**HD**" menu by mistake?
* In Blender, diffeomorphic daz importer's global setting, make sure you have set Daz lib path with "**Load Root Path**" button.
* Does this vmd motion use IK? If not, set IK to Off before importing.
* In Blender, Right side, Scene panel, Units section, make sure it is set to 1 Metre.  
* Try another vmd motion from a different author. 

If only this author's vmd motion can not be imported correctly, contact us, tell us the name of this vmd motion, we will test it.  


## shift_jis error
If there is error msg with `shift_jis` in it, it means, this vmd file is not encoded with `shift_jis`.   

You need to open MMD, load a TDA model, load this vmd file and Re-save it into a new vmd file. This new vmd file will be encoded with `shift_jis`. Then import this new vmd file.  

## Eye can not be fully closed
MMD model comes with 5 morphs can close eyes. But other character like Daz or CC only has one morph to close eye.  

Normally, vmd motion's creator only use 1 of those 5 morphs to close eye, to avoid chaos. But, there are a few vmd motion's creator will play with all 5 morphs.    

In that case, all 5 mmd morphs data is converted into 1 daz/cc morph, so one morph's data will cover another, which make eyes can not be fully closed.  

The only solution for this, is remove all other 4 morphs' data in MMD, only keep one of them.  

These 5 morphs are: ウィンク, ウィンク２, まばたき, 笑い, なごみ  

or you can just remove all 5 morphs' data.  

## Daz Studio Setting for importing motion
We created a video tutorial for exporting motion and importing into Daz Studio.  
[https://youtu.be/FEA9hVouKFg](https://youtu.be/FEA9hVouKFg)  

But, there is one important setting hasn't been mentioned in that video.  

In Daz Studio, Genesis 8 has **hidden and locked** x, y, z rotation properties on every bone. As following picture shows.  
![locked_xyz_rotation_properties](img/locked_xyz_rotation_properties.jpg)  

The exported daz pose preset from blender need to use those properties. So, you need to **make them visible then unlock those x,y,z rotation properties on every bone** in Daz Studio, before you load that pose preset. As following picture shows.  
![unlocked_xyz_rotation_properties](img/unlocked_xyz_rotation_properties.jpg)  

To unhide those properties, go to parameter pan's option menu->"Preferences"->"Show Hidden Properties", check it. As following picture shows.  
![show_hidden_property](img/show_hidden_property.jpg)

Then, unlock all **x, y, z rotation properties** on every bone. Only rotation properties. 
![unlocked_xyz_rotation_properties](img/unlocked_xyz_rotation_properties.jpg)  

This is a Daz's bad design for G3 and G8. If you need to import any pose data into Daz, you need to unlock those hidden properties.  

It is insane to do this on every Daz Character. So, people already created a Daz script to unlock them.  

Download following daz script:    
[https://www.dropbox.com/s/pjojvrnymcdi388/](https://www.dropbox.com/s/pjojvrnymcdi388/)  

In Daz Studio, select your G8 character, then run this script, done. Now you can import pose preset.   

If one day, above download link fails, you can get new link from its release video:  
[https://www.youtube.com/watch?v=wHiKCx8nj5k](https://www.youtube.com/watch?v=wHiKCx8nj5k)  




# Update Log:
## 1.24.0
* Add Important new feature: Create and Clear Proxy Mesh

## 1.23.0
* Add "Clear Animation" Button

## 1.22.0
* Re-map waist bone, now it is treated as a layer of hip bone, like center and groove bone. Also, when importing motion from vmd file directly, it gonna be on a different track on NLA.  

## 1.21.0
* When using a MMD model as motion source, upper body now is retargeted from MMD's final bone rotation in world space, not local space. Which means, it can handle layered MMD bones(Like shoulder P and twist bones) better. But addon's Arm rotation rate and euler plus won't work in this way any more.  

## 1.20.2
* Ignore ik bones when IK is not used in vmd file

## 1.20.0
* Add ik parent bones and foot ik bones to have a full mmd style ik system. If you get problem on feet, check "High Heel", will bring back the old way.  

## 1.19.1
* add bending to knee for cc3 model, to fix ik issue.

## 1.19.0
* Support Genesis 9 for diff daz importer

## 1.18.3
* Fix hand rest pose
* Add "Reuse generated texture" option to "Daz to MMD"

## 1.18.2
* Remove IK limits for DTB 2022
* Fix toe issue for "Daz to MMD" when shoes are separated 2 meshes(left and right shoe).

## 1.18.0
* Modify converting method, to use Current pose as Rest Pose. Which can fix poking issue of forearms. Now addon converts vmd motion in the same way as blender mmd tools.
* Allow using thigh rotation with IK together, to handle knees since there is no IK Pole bone anymore. Blender mmd tools handle knees in the same way.
* Add button to check new version. 
* Add Rig section and Daz to MMD button, to convert Daz model into MMD model with 1 click.  

## 1.14.1
* Set shin bone's IK stiffness to 0 for DTB 2022

## 1.14.0
* Use rotation limit to replace IK Pole Bone
* Change Daz model's arm rest difference degree from 10 to 8

## 1.13.0
* Add Euler setting for forearm's rotation
* Fix a bug when loading IK states from vmd file.

## 1.12.0
* Read interpolation from vmd file(Bone rotation only)

## 1.11.0
* Add an option to turn IK on or off automatically

## 1.10.0
* Add url button to document and feedback issue list

## 1.9.0
* Support IK親 bones. IK親 means IK Parent bones, aka IKP bone. Now, Fairy Tale's vmd motion works. For example, vmd motion: "AOA - like a cat".

## 1.8.0
* Support the new Daz to Blender Bridge 2022, check document for more.

## 1.7.1
* Check Blender version

## 1.7.0
* Support CC4

## 1.6.4
* Update UI with boxes
* Go to Object mode when executing to prevent user run it in Edit mode
* Remove Debug mode button, add a label for addon version

## 1.6.3
* Set "ぺろっ" and "口角上げ"'s converting rate to 0.5, to make a better smile.
* Handle "shift_jis" error to show a msg.
* Fix an issue that can not import camera when using DTB character.

## 1.6.0
* Support Daz model imported by Official Daz to Blender Bridge:
[https://github.com/butaixianran/DazToBlender](https://github.com/butaixianran/DazToBlender)  

## 1.5.0
* Convert twist bone and Waist bone

## 1.4.1
* Support Blender 3.1
* Add shoulder rotation rate

## Older
* Set Arm rotation rate to 0.8 as default, since every vmd motion put hands to chest.
* Add shoulder rotation rate then remove it, seems not very useful.
* Add IK checkbox, uncheck to not create IK bones.
* Handle rotation for center bone
* Remove leg's rotation when importing from vmd file since IK takes control
* Fix feet rotation when retargeting from mmd model
* Arm rotation rate now works when retargeting motion from a mmd model
    - This is done by using a new way to convert mmd model's upper body motion
* When executing with a wrong model type, now shows a message.