### 对于Ubuntu 16.10和Ubuntu 17.04，通过Ctrl + Alt + T打开终端，或通过从应用启动器搜索“terminal”，打开后，执行以下步骤：

1. .通过命令添加PPA存储库：
`sudo add-apt-repository ppa:mystic-mirage/pycharm`
***
2.如果您安装了以前的版本，请通过软件更新程序升级PyCharm。
##### 运行命令来检查更新并安装IDE（社区版本）
`sudo apt update`
`sudo apt install pycharm-professional`
***
##### 或运行命令来检查更新并安装IDE（社区版本）：
`sudo apt update`
`sudo apt install pycharm`
***
3.卸载PyCharm：
要卸载PyCharm Python IDE，只需运行命令：
专业版:  `sudo apt remove --autoremove pycharm pycharm-professional`  
社区版:   `sudo apt remove --autoremove pycharm pycharm-community`  
