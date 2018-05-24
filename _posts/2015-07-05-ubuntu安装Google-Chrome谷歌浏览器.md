# ubuntu三行命令安装chrome浏览器

安装谷歌浏览器，只需要三行代码：
按下 Ctrl + Alt + t 键盘组合键，启动终端。
输入以下命令：
`cd /tmp `
对于谷歌Chrome32位版本，使用如下链接：
`wget [https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb)`

对于64位版本可以使用如下链接下载：
`wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)`

下载完后，运行如下命令安装
32 位安装命令:
`sudo dpkg -i google-chrome-stable_current_i386.deb`

64 位安装命令:
`sudo dpkg -i google-chrome-stable_current_amd64.deb`
或
`sudo dpkg -i google-chrome*`
`sudo apt-get -f install`

#为chrome安装Flash播放器插件

屏幕右上角，“系统设置”–>“软件和更新”–>“其它软件”
勾选“Canonical合作伙伴”
点击“关闭”
终端输入：

`sudo apt install adobe-flashplugin`

#添加 Google Chrome 的PPA
安装Google Chrome浏览器官方PPA，打开终端然后运行下面的命令，下载签名密钥：

`wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add`

`sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'`

`sudo apt-get update`

`sudo apt-get install google-chrome`
