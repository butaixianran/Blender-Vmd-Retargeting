#### Note: This function is for senior content creator. You should be familiar with Blender or PE Editor's modeling, skeleton and material functions. It's not for newbie.   

# Language
[中文](daz_to_mmd.cn.md)  

# Daz to MMD
This function will convert a daz character into a MMD character with one click. Then you can export it into .pmx file and use it in MMD.  

# Supported model type
* G8 and G8.1. 

# Supported blender version
* For now, blender 3.x only
* For Blender 4.x, we need to wait Blender MMD addon supports blender 4.x.

# Download and Install
This is a part of Vmd Retargeting blender addon.   
[https://blendermarket.com/products/vmd-retargeting](https://blendermarket.com/products/vmd-retargeting)  

# How to use
There are 2 ways, pick one.  

## With Diffeomorphic daz importer
### Prepare Addon
You need to install following blender addons to make this work.
* [Blender mmd tools](https://github.com/UuuNyaa/blender_mmd_tools)
* [Diffeomorphic daz importer](https://bitbucket.org/Diffeomorphic/import_daz/wiki/Home)

In Diffeomorphic daz importer Blender addon's global setting, right-up corner, **set material setting to use Single reused Principled Shader**. Default setting is iray shader, which won't work in this case.  

If you use eevee, go to render panel, check **Screen Space Reflection** and check **Refraction**.  

### Prepare model
#### Daz Side
Load a G8 model. Use Diffeomorphic daz importer's script to export.  

When exporting, **Do not** choose "Export to Blender **HD**", use the one without HD in it.   

#### Blender Side
Go to Diff daz import addon's **Global Setting**. At the "Rigging" Section, there are following check boxes:  
"Location Locks, Location Limits, Rotation Locks, Rotation Limits"    
Make sure they are **unchecked**.   
![](img/rigging.jpg)  

Then, use diff daz import addon's "**Easy Import Daz**" to import your character.  

When importing, check "**Merge Rigs**", "**Face Units**", "**Visemes**".   

By default, diff daz import use facial bones for facial motion, but MMD need shape keys. So you need to convert morph into shape keys here.  

After importing, select character's **body mesh**, go to diff daz import addon's panel:  
`Advanced Setup` -> `Morphs` -> `Convert Morphs To Shapekeys`.  

Check "All" at left-up corner, check "Labels As Names" checkbox at bottom, then click OK.  

### Convert
**Select Armature**, go to **Vmd Retargeting** addon's panel. At bottom, Rig section, Click "**Daz to MMD**" and wait. After it's done, now this is a MMD model.  

Then go to menu: `File->export->.pmx`. At option area, set scale to 11. Done.  


## With Daz For Blender Bridge Addon
### Prepare addon
You need to install following blender addons to make this work.
* [Blender mmd tools](https://github.com/UuuNyaa/blender_mmd_tools)
* [Diffeomorphic daz importer](http://diffeomorphic.blogspot.com/p/daz-importer-version-16.html)
* [Daz For Blender](https://github.com/butaixianran/DazToBlender)

**Daz For Blender** is a modified version from Daz's official DTB 2022. It offers a lot of things the official DTB 2022 doesn't have. And this addon need that.   

You better use it at blender side and still use the Daz's official DTB 2022 at Daz side.   

### Prepare model
#### Enable G8 morph on G8.1
If you wan to use G8.1 character with this addon. You need to enable G8 facial morphs on G8.1.  

By default, Daz disabled G8 morphs on G8.1 and hide them from user. You need to get them back.  

Check this post at Daz forum for this:  
[https://www.daz3d.com/forums/discussion/533161/mouth-open-for-genesis-8-1-female](https://www.daz3d.com/forums/discussion/533161/mouth-open-for-genesis-8-1-female)  

This is not needed for G8.  

#### Daz Side
Set G8 model to default A-Pose, no animation.  

Use Daz's official DTB 2022 to export your character.   

When exporting, you need to **check export morph**. And add following morph section into exporting list.  
`Pose Control-> Head -> Eye, Mouth, Brow, Viseme.`

Then export.  

#### Blender Side
Use **Daz for Blender** addon to import your character.  

**Uncheck "Use Driver" and "Custom Shape" before importing**.  

### Convert
**Select Armature**, go to **Vmd Retargeting** addon's panel. At bottom, Rig section, Click "**Daz to MMD**" and wait. After it's done, now this is a MMD model.  

Then go to menu: `File->export->.pmx`. At option area, set scale to 11. Done.


# Common Issue
## Push morph
When using Daz character with dance animation, body may poke through clothes. So, this addon creates push morphs on every wearable meshes. 

This push morph, can scale clothes a little bigger to eliminate poking. And they can be used in MMD.  
This morph is created by using "Diffeomorphic daz importer"'s operator.  

## Alpha issue
Daz's alpha texture uses gray color for alpha. But mmd can only handle binary alpha(Black or white).  
So, you'll never get Daz's hair works well in MMD.  

You can try to convert Daz's alpha texture into a binary image. But it only works on single layer hair mesh. With layered hair mesh, it still won't work well.  

I'm not very good at photoshop or modeling. So, if you are a senior content creator, you may find a solution. If you do, you are welcome to share it with us.  

## Rotation issue
Daz character comes with different bone structure, so forearm may poke into body in some cases. You need to use multiply value function in mmd to adjust the rotation of forearms.  

Normally, 0.8-0.9 for forearms is a good value to try.  




