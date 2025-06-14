# Website

我们需要建立一个以各种蘑菇为背景的静态html，不要太密集，页面主题是Mycelium协议白皮书，介绍MushroomDAO。
包括四个部分白皮书、里程碑、DAO、GToken，分别是四个简单的自然和人的插画，对应了这四部分内容介绍。
白皮书是介绍我们的思考和研究，包括对社会问题的思考和探索方案，收入的一些技术细节，商业落地介绍；以及相关的技术和社会研究的文档集合。
里程碑是指作为一个协议，整体的目标和关键里程碑规划，秉持开放态度，完成基建后是一个开放花园生态。
而GToken指的是协议的Token机制，包括治理Token和开放的OpenPNTs协议，任何组织和个体都可以发行自己的Token，以及基于协议为MushroomDAO发行的mPNTs。
而DAO部分是介绍这个DAO的组织结构和开放协作的基础模式，包括构建协作和互操作的一些协议和产品。
请帮我设计一个独立静态页面，背景是可爱的各种蘑菇，以及上述四个插画，链接到四个页面（markdown文档）。

## Logo
:mushroom:
:mushroom:
:mushroom:
🍎🍐🍊🍋🍉🍇🍈🍄
U+1F344
```
:mushroom:
```
## Design
设计特点
视觉设计：

渐变背景色彩，营造现代科技感
可爱的蘑菇背景装饰，符合主题
玻璃拟态效果的卡片设计
响应式布局，适配各种设备

四个核心部分：

白皮书 - 文档图标，紫色渐变
里程碑 - 星星图标，粉红渐变
GToken - 代币图标，蓝色渐变
DAO - 社区图标，绿色渐变

🚀 交互功能

卡片悬停动画效果
插画旋转缩放动画
蘑菇背景浮动动画
卡片渐现进入效果
平滑滚动导航

📱 技术特性

完全静态HTML页面
纯CSS动画，性能优秀
响应式网格布局
无需外部依赖库
SEO友好的语义化标签

 语言功能
自动检测语言：

根据浏览器语言设置自动选择中文或英文
中文浏览器默认显示中文，其他语言默认显示英文

语言切换：

右上角语言切换按钮
平滑的语言切换动画
支持键盘快捷键 Alt + L 快速切换

📋 内容组织
中文版本：

链接到 *-zh.md 文件 (如 whitepaper-zh.md)
完整的中文界面和描述

英文版本：

链接到 *-en.md 文件 (如 whitepaper-en.md)
专业的英文翻译和描述

🎨 技术特性
智能语言管理：

使用 LanguageManager 类管理语言状态
自动更新页面标题和HTML语言属性
保持动画效果在语言切换时的连贯性

增强的动画系统：

AnimationManager 类管理所有动画效果
交叉观察器实现渐入动画
交互式悬停效果和蘑菇背景动画

响应式设计：

移动端优化的语言切换器
适配各种屏幕尺寸
保持在所有设备上的一致体验

## Document
whitepaper-zh.md / whitepaper-en.md
milestones-zh.md / milestones-en.md  
gtoken-zh.md / gtoken-en.md
dao-zh.md / dao-en.md
