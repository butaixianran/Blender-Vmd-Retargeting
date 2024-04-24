#### 注意: 本功能是为有经验的模型制作者准备的。用户需要熟悉Blender或者PE Editor的建模，骨骼和材质功能。本功能不适合新手。新手硬要尝试的话，来问任何入门问题均不会理睬。  

# Daz to MMD
本扩展能一键转换Daz人模为MMD人模，然后可以导出.pmx模型用于mmd。

# 支持的模型类型
* G8和G8.1.  

# 支持的Blender版本
* 暂时只支持Blender 3.x。
* Blender 4.x暂不支持，等待Blender MMD扩展支持Blender 4.x。

# 下载和安装
本功能现在是Vmd Retargeting扩展的一部分。  
爱发电下载：  
[https://afdian.net/item/44e30d86d2c311ed9a2c5254001e7c00](https://afdian.net/item/44e30d86d2c311ed9a2c5254001e7c00)  
购买后会有站内信，内有网盘下载地址。 

Blender市场（推荐）：  
[https://blendermarket.com/products/vmd-retargeting](https://blendermarket.com/products/vmd-retargeting)   


# 使用方法
有两种方法，任选其一。  

## 使用Diffeomorphic daz importer扩展
### 准备扩展
你需要安装如下Blender扩展
* [Blender mmd tools](https://github.com/UuuNyaa/blender_mmd_tools)  
* [Diffeomorphic daz importer](https://bitbucket.org/Diffeomorphic/import_daz/wiki/Home)  

前往Diffeomorphic daz importer Blender扩展的全局设置，右上角，材质设置区域，**设置为使用Single reused Principled Shader**。原本的设置是用iray shader，那样是无法顺利转换的。  

如果你使用eevee，前往渲染设置面板，勾选 **Screen Space Reflection**(屏幕空间反射) 和 **Refraction**（屏幕空间折射）。  

### 准备人模
#### Daz一侧
加载G8人模，使用Diffeomorphic daz importer的脚本导出人模。   

导出的时候，**不要**选择"Export to Blender **HD**"，用没有HD的那个菜单导出。     

#### Blender一侧
首先，进入diff daz import扩展的全局设置(Global Setting)。在中间"Rigging"区域，有4个勾选框：  
"Location Locks, Location Limits, Rotation Locks, Rotation Limits"  
这些默认应该是没有勾选的。如果你的设置中是勾选的，要去掉勾选。不然手脚运动都会被限制住。  
![](img/rigging.jpg)  

然后，使用diff daz import扩展的"**Easy Import Daz**"按钮导入人模。  

导入时，勾选："**Merge Rigs**", "**Face Units**", "**Visemes**".  

默认，diff daz import使用面部骨骼来处理面部动作。而MMD需要用变形。所以，这里要进行转换。

导入后，选择人模的**身体模型**，不是骨架。前往diff daz import扩展面板:  
`Advanced Setup` -> `Morphs` -> `Convert Morphs To Shapekeys`.  

打开的窗口，左上角，点击All，底部，勾选"Labels As Names"，然后点击确定。  


### 转换
**选择人模骨架**，前往**Vmd Retargeting**扩展面板。底部，Rig区域，点击"**Daz to MMD**"按钮，并等待。完成后，这就是个MMD模型了。  

接下来，前往菜单: `File->export->.pmx`. 导出选项上，scale比例改为11。完成。  


## 使用Daz For Blender Bridge扩展
### 准备扩展
你需要安装以下扩展。本扩展会自动调用这些扩展中的功能。
* [Blender mmd tools](https://github.com/UuuNyaa/blender_mmd_tools)
* [Diffeomorphic daz importer](http://diffeomorphic.blogspot.com/p/daz-importer-version-16.html)
* [Daz For Blender](https://github.com/butaixianran/DazToBlender)

**Daz For Blender** 是Daz官方的DTB 2022的修改版。提供了官方没有的很多功能，这里需要用到。  

你最好在Daz一侧使用官方的DTB 2022，而在Blender一侧使用我们修改的 Daz For Blender扩展版本。    

### 准备人模
#### 在G8.1上启用 G8 Morph [G8不用]
如果你要把G8.1用于本扩展，你必须在G8.1上，启用G8的表情。  

默认，Daz在G8.1上，关闭了G8表情，并且隐藏了起来。你需要把他们找回来。  

方法查看Daz论坛的这个帖子:  
[https://www.daz3d.com/forums/discussion/533161/mouth-open-for-genesis-8-1-female](https://www.daz3d.com/forums/discussion/533161/mouth-open-for-genesis-8-1-female)   

G8不需要做这些事情。   

#### Daz一侧
加载G8人模，使用Daz官方的DTB 2022导出人模。   

导出的时候，勾选**export morph**。然后，添加下面的一系列morph到导出列表中：  
`**Pose Control**-> Head -> Eye, Mouth, Brow, Viseme.`  然后导出。   

### Blender一侧
使用**Daz for Blender**扩展导入人模。
导入之前，**去掉勾选 "Use Driver" 和 "Custom Shape"**。完成。  

### 转换
现在，**选择人模骨架**，前往**Vmd Retargeting**扩展面板。底部，Rig区域，点击"**Daz to MMD**"按钮，并等待。完成后，这就是个MMD模型了。  

接下来，前往菜单: `File->export->.pmx`. 导出选项上，scale比例改为11。完成。  

# 常见问题
## Push 变形
当使用Daz人模来跳舞的时候，衣服和身体可能会互相穿模。所以，本扩展会给所有可穿戴模型（衣服鞋子头发），添加一个Push变形。  

这个Push变形，能稍微把衣服放大一点点，从而解决穿模。这个变形可以在mmd中作为表情使用。  

该变形使用"Diffeomorphic daz importer"的功能创建。  

## Alpha问题
Daz的alpha贴图使用灰色作为自然过渡。但MMD只能处理二值alpha（黑白）。所以，Daz的头发在mmd中永远无法很好的呈现。  

你可以转换Daz的alpha贴图为二值黑白图片。但是也只能在单层头发模型上有合理效果。对于多层的头发模型，还是无法良好呈现。  

我也不是photoshop和建模高手。如果你是资深建模师，你可能有办法解决这个问题。如果你找到了解决办法，欢迎来和我们分享。  

## 旋转问题
Daz人模整个骨架设计，和mmd有太多不同。所以很多舞蹈动作中，多多少少会有一点穿模。所以，你需要用mmd的关键帧倍乘功能，来调整前臂的旋转。  

一般来说，前手臂乘以0.8-0.9，是个比较合理的范围。  
