# VPet-Simulator - dev branch

開發用分支，容易出bug，慎用

### 开源

该游戏在github上开源, 欢迎提出自己的想法,创意或者参与开发!<br/>
您还可以修改代码来制作自己专属的桌宠!(虽然说大部分内容都支持创意工坊,不需要修改代码)<br/>
原项目地址: https://github.com/LorisYounger/VPet

### 支持创意工坊

该游戏支持创意工坊,您可以制作别的人物桌宠动画或者互动,并上传至创意工坊分享给更多人使用.

创意工坊支持添加/修改以下内容

* 桌宠动画
* 物品/食物/饮料等
* 自定义桌宠工作
* 说话文本
* 主题
* 代码插件 - 通过编写代码给桌宠添加内容
  * 添加新的动画逻辑/显示方案 (eg: l2d/spine 等)
  * 添加新功能 (闹钟/记事板等等)
  * 几乎无所不能, 示例例子参见 [VPet.Plugin.Demo](https://github.com/LorisYounger/VPet.Plugin.Demo)

## 软件结构

* **VPet-Simulator.Windows: 适用于桌面端的虚拟桌宠模拟器**
  * *Function 功能性代码存放位置*
    * CoreMOD Mod管理类
    * MWController 窗体控制器
  
  * *WinDesign 窗口和UI设计
    * winBetterBuy 更好买窗口
    * winCGPTSetting ChatGPT 设置
    * winSetting 软件设置/MOD 窗口
    * winConsole 开发控制台
    * winGameSetting 游戏设置
    * winReport 反馈中心
  
  * MainWindows 主窗体,存放和展示Core
  * PetHelper 快速切换小标
* **VPet-Simulator.Tool: 方便制作MOD的工具(eg:图片帧生成)**
* **VPet-Simulator.Core: 软件核心 方便内置到任何WPF应用程序(例如:VUP-Simulator)**
  * Handle 接口与控件
    * IController 窗体控制器 (调用相关功能和设置,例如移动到侧边等)
    * Function 通用功能
    * GameCore 游戏核心,包含各种数据等内容
    * GameSave 游戏存档
    * IFood 食物/物品接口
    * PetLoader 宠物图形加载器
  * Graph 图形渲染
    * IGraph 动画基本接口
    * GraphCore 动画显示核心
    * GraphHelper 动画帮助类
    * GraphInfo 动画信息
    * FoodAnimation 食物动画 支持显示前中后3层夹心动画 不一定只用于食物,只是叫这个名字
    * PNGAnimation 桌宠动态动画组件
    * Picture 桌宠静态动画组件
  * Display 显示
    * basestyle/Theme 基本风格主题
    * Main.xaml 核心显示部件
      * MainDisplay 核心显示方法
      * MainLogic 核心显示逻辑
    * ToolBar 点击人物时候的工具栏
    * MessageBar 人物说话时候的说话栏
    * WorkTimer 工作时钟

## 参与开发

請見原repo: https://github.com/LorisYounger/VPet

## 动画版权声明与授权

在github中 [桌宠动画文件](https://github.com/LorisYounger/VPet/tree/main/VPet-Simulator.Windows/mod/0000_core/pet/vup) 动画版权归 [虚拟主播模拟器制作组](https://www.exlb.net/VUP-Simulator)所有, 当使用本类库时,您可能需要自行准备动画文件,或遵循以下协议

### 非商用用途授权

* 需要向用户告知动画文件来源并提供访问 [该页面](https://github.com/LorisYounger/VPet) 的链接
* 当您完成以上要求后,您可以免费使用动画文件

### 商用用途授权(低于10万)

* 第一次使用时需弹窗并醒目的向用户告知动画文件来源并提供访问 [该页面](https://github.com/LorisYounger/VPet) 的链接
* 在相应页面(用户可以快捷访问)向用户告知动画文件来源并提供访问 [该页面](https://github.com/LorisYounger/VPet) 的链接
* 当您完成以上要求后,您可以免费使用动画文件

### 商用用途授权(高于10万或其他)

* 请[邮件联系](mailto:zoujin.dev@exlb.org)原作者

### 分发动画文件

* 需要告知以上所有授权信息
* 需要提供访问 [该页面](https://github.com/LorisYounger/VPet) 的链接
* 分发动画文件时禁止任何付费/收费行为

## 桌面端部署方法

1. 下载本项目, 通过VisualStudio打开 `VPet.sln` 文件
2. 在生成栏中, 选择 位数为 `x64` 和生成项目为 `Vpet-Simulator.Windows`
   ![image-20230208004330895](README.assets/image-20230208004330895.png)
3. 点击启动, 如果一切正常则会报错 `缺少模组Core,无法启动桌宠`
4. 以管理员身份运行 `mklink.bat`, 这会让mod文件链接到生成位置
5. 再次点击启动即可正常运行
