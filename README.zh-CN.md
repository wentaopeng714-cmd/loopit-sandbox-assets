# 沙盒游戏素材库 / Sandbox Field Kit

为 Loopit 的“采集资源—制作建造—提升生存能力”方向整理。美术采用同一作者 Kay Lousberg 的明亮低多边形系列。不是白膜，也不是完整游戏。

## 已整理的内容
- 603个模型GLB文件（包含颜色、造型和不同动作版本，不能理解为603种互不重复的物件）。
- 4个基础角色加1个兜帽造型变体：Barbarian、Knight、Mage、Rogue、Rogue Hooded。
- 每个角色有原版、完整171片段版、轻量20片段版。轻量版每个约1.0–1.1MB；完整动作版约10MB，建议游戏首屏先加载轻量版。
- 105个森林植被/岩石，49个工具/配件，76个资源模型，221个地形/建筑/营地模块，53个家具，57个太空基地模块，27个角色配件。
- 三张拼装好的静态场景GLB：森林营地、村庄工坊、太空前哨。附JSON摆放清单，可直接加载整场景，也能按原始模型重新布置。

## 怎么查看
已运行的预览：http://127.0.0.1:8773/
也可以在本文件夹运行 `python3 -m http.server 8773`，再打开这个地址。不能用file://直接双击HTML加载GLB。
预览中可以切换场景、角色和真实动画，搜索并单独查看模型，下载当前GLB。预览不是采集或建造游戏，当前没有游戏进度。

## 给Loopit使用
先选择一个轻量角色和一个场景，不要一次加载整个素材库。例如：
- models/characters-lite/rogue-survival-lite.glb
- scenes/forest-camp.glb
- models/tools/axe.glb
- models/resources/Wood_Log_A.glb

模型均为自包含GLB，保留原模型、材质和贴图。用GLTFLoader读取，再用AnimationMixer播放精确片段名，如 Chopping、Pickaxing、Hammering、Digging、PickUp。不要用生成的简易角色替代真实模型。所有片段名和来源见manifest.json及动作对照表。

场景GLB是静态环境，不带碰撞体、导航、采集点、资源掉落、建造规则、天气或存档。树木倒下、建造出现和升级变化等需要游戏代码实现。这样能让角色和环境独立加载与替换。

## 目录
- models/characters-lite：推荐先用，20条常用动作。
- models/characters-ready：完整171片段版本。
- models/characters：保留原始76片段角色，含T-Pose和静态姿势。
- models/forest、tools、resources、medieval、furniture、space、accessories：按功能分类。
- scenes：3个完整环境GLB和JSON实例清单。
- animations：作者Rig_Medium分类动作GLB原件。
- 素材清单.csv、场景清单.csv：中文分类、大小、面数、来源及版本固定的GitHub直链。
- licenses、SOURCES.md：授权原文和作者来源。

## 授权
本次选用的美术和动作均为作者免费包，授权原文均为CC0。保留作者和来源是为了方便后续维护。预览页代码另按MIT授权。没有加入付费EXTRA/SOURCE内容，也没有将只允许用于成品的资产包重新打包。

## 处理方式
静态glTF的外部bin与PNG已合并到GLB，几何和贴图不重绘；角色保持原绑定，额外动画按相同骨骼名称合并。轻量版删除未使用动画数据，保留几何、蒙皮和材质。三个环境由本项目用这些原始模型拼装。

完整/轻量动作版已从默认场景移除原版预设武器网格（如弩、盾），保留身体、外观、帽子、披风、贴图、蒙皮和骨骼，避免拿斧头时还同时背出一把弩。原版角色文件不改，武器附件也单独保留。
