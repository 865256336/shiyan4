# shiyan4
实现基本的图像分类APP
实验内容
按照教程构建基于TensorFlow Lite的Android花卉识别应用。
• 查 看 该 应 用 的 代 码 框 架 ， 特 别 注 意 CameraX 库(AndroidX.camera.*)和数据视图模型的使用。
• 上 传 完 成 既 定 功 能 的 代 码 至 Github ， 并 撰 写 详 细 的Readme文档
实验步骤
首先安装Android Studio 4.1以上的版本
• 下载代码ZIP或者使用git clone克隆代码
• 导入已有的Tensorflow Lite模型（finish模块ml文件夹下的FlowerModel.tflite）
• 按照教程完成所有TODO代码项
• 真机运行完成的花卉识别应用
打开Android Studio，选择“Open an Existing Project”
选择TFLClassify/build.gradle生成整个项目。项目包含两个module：finish 和 start，finish模块是已经完成的项目，start则是本项目实践的模块。
手机通过USB接口连接开发平台，并设置手机开发者选项允许调试
选择真实物理机
允许应用获取手机摄像头的权限，得到下述效果图，界面利用随机数表示虚拟的识别结果
![image](https://github.com/865256336/shiyan4/assets/107561613/3607ee72-1544-4654-9004-dd9ec5bc1469)
选择"start"模块
![5278e7e8d7ac4959b25af003302ac8fb](https://github.com/865256336/shiyan4/assets/107561613/170eae89-0b8e-4dc6-9d19-88e128ba7b9b)
右键“start”模块，或者选择File，然后New>Other>TensorFlow Lite Mode
![243e408549fb4ead9f691fa14cb7909b](https://github.com/865256336/shiyan4/assets/107561613/bd1b91c0-d8c4-4537-93b0-7707cdb960b7)
选择已经下载的自定义的训练模型。本教程模型训练任务以后完成，这里选择finish模块中ml文件下的FlowerModel.tflite
![6c950eab16754d398ddd8d619ba91dda](https://github.com/865256336/shiyan4/assets/107561613/b3a0e221-376c-44cd-beab-020322ea1778)
点击“Finish”完成模型导入，系统将自动下载模型的依赖包并将依赖项添加至模块的build.gradle文件。
TensorFlow Lite模型被成功导入，并生成摘要信息
![dfb323903f814bf0a1eed1c2c249f233](https://github.com/865256336/shiyan4/assets/107561613/03ce745a-fa69-445d-ba19-8a8c84b60eff)
本项目初始代码中包括了若干的TODO项，以导航项目中未完成之处。为了方便起见，首先查看TODO列表视图，View>Tool Windows>TODO
![877f623a4d57470bb67688bd40d2bb71 (1)](https://github.com/865256336/shiyan4/assets/107561613/afbb49f4-8d53-4f61-8746-d60f63f7fc63)
默认情况下了列出项目所有的TODO项，进一步按照模块分组（Group By）
![f202e02285cb48e698910662448baf3d (1)](https://github.com/865256336/shiyan4/assets/107561613/db147f98-eb6e-4c50-b830-295970787d36)
定位“start”模块MainActivity.kt文件的TODO 1，添加初始化训练模型的代码
在CameraX的analyze方法内部，需要将摄像头的输入ImageProxy转化为Bitmap对象，并进一步转化为TensorImage 对象
对图像进行处理并生成结果，主要包含下述操作：
按照属性score对识别结果按照概率从高到低排序
列出最高k种可能的结果，k的结果由常量MAX_RESULT_DISPLAY定义
将识别的结果加入数据对象Recognition 中，包含label和score两个元素。后续将用于RecyclerView的数据显示
将原先用于虚拟显示识别结果的代码注释掉或者删除
以物理设备重新运行start模块
![image](https://github.com/865256336/shiyan4/assets/107561613/189b4df0-a2c4-4094-b3e4-33c84f78fed1)
