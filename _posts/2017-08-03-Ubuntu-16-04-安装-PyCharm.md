Ubuntu 16.04已经自带了Python，然后要安装一个Python IDE，上网查了一下，推荐的有10个之多（链接：[http://www.runoob.com/w3cnote/best-python-ide-for-developers.html](http://www.runoob.com/w3cnote/best-python-ide-for-developers.html)），有PyCharm、Komodo Edit、PyScripter、The Eric Python IDE等等，根据网上的推荐，最后选了PyCharm。

下面开始教程

先在PyCharm官网下载安装包

链接：[https://www.jetbrains.com/pycharm/download/#section=linux](https://www.jetbrains.com/pycharm/download/#section=linux)

选择平台为Linux，可以看到当前版本为2017.1.4，这里分为Professional专业版和Community社区版，区别是专业版是收费，而且功能更多，具体是什么功能我就没仔细了解了

我选择的是Professional专业版，直接点击DOWNLOAD下载就行了

![image](http://upload-images.jianshu.io/upload_images/9135759-d9937acdd1186034?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

下载完成后，安装包在Downloads文件夹下

![image](http://upload-images.jianshu.io/upload_images/9135759-f321595658f3fe19?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

右键安装包，点击“Extract Here”意思是提取到这里，相当于解压

![image](http://upload-images.jianshu.io/upload_images/9135759-227aa533243a6555?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

提取完成后，会生成一个pycharm-2017.1.4的文件夹

![image](http://upload-images.jianshu.io/upload_images/9135759-12b5c26e005f0255?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在终端指定到pycharm-2017.1.4/bin目录下

输入“cd Downloads/pycharm-2017.1.4/bin”

![image](http://upload-images.jianshu.io/upload_images/9135759-3b29c320bab2b804?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

执行sh命令，打开安装

输入“sh ./pycharm.sh”

![image](http://upload-images.jianshu.io/upload_images/9135759-30f538a2f3cfcc60?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

回车后，大概等待十几秒（我的虚拟机比较卡…），出现Complete Installation弹框，

如果需要导入之前安装版本的配置的话，就选第一个，没有就选第二个。

所以这里选第二个，直接点击OK即可

![image](http://upload-images.jianshu.io/upload_images/9135759-95d81ee8ec0ca4ae?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击OK之后弹出 PyCharm Privary Policy Agreement框，隐私政策协议，直接点击Accept 同意即可
![image](http://upload-images.jianshu.io/upload_images/9135759-b65eddd28bf14dea?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

然后会弹出PyCharm License Activation框，PyCharm许可证激活

Activation license with 激活许可证选择：License server

License server address许可证服务器地址填：http://idea.imsxm.com

然后点击“Activate”即可

![image](http://upload-images.jianshu.io/upload_images/9135759-2b343dcf5bba2958?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

进入正在安装界面，等待安装完成

![image](http://upload-images.jianshu.io/upload_images/9135759-a3252a7fe5cb1de0?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

安装完成后，会弹出PyCharm Initial Configuration框，PyCharm初始化配置

Keymap scheme：键盘方案，选择Eclipse，意思是设置Pycharm为Eclipse快捷键

ide theme：皮肤主题，默认Intellij。可根据自己喜欢选其他的

Editor colors and fonts：编辑器的主题，可以点击下面的“Click to hide preview”进行预览，我这里选择的是 Darcula

然后下面的Create desktop entry 默认打勾就行了

最后点击OK，完成设置
![image](http://upload-images.jianshu.io/upload_images/9135759-a001316fd0ad3bdc?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

完成安装及配置
![image](http://upload-images.jianshu.io/upload_images/9135759-9995c6339caabdb9?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击Craete New Project，创建一个新的项目

左边的列表选“Pure Python”

Interpreter选择安装的3.6.1版本
![image](http://upload-images.jianshu.io/upload_images/9135759-fcfca0a96e36d777?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

开始Python的编程之旅吧~~
