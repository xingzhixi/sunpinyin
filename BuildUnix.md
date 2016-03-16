# 依赖组件 #

为了编译SunPinyin基本库你需要安装以下的工具

  * C++编译器 (sudo aptitude install build-essential)
  * sqlite3 (sudo apt-get install sqlite3 libsqlite3-dev)
  * SCons  (sudo apt-get install scons)

如果你偏好ibus，可以安装ibus-wrapper，你需要
  * ibus > 1.2
  * gettext

如果你偏好最简单的xim，可以安装xim-wrapper，你需要
  * gtk > 2.10
  * x11的所有头文件

# 安装方法 #

SunPinyin 分为三部分。
  * 后端：就是 SunPinyin 输入法内核/引擎，它负责 SunPinyin 的算法和提供最基本的输入法功能，在 GNU/Linux 上它以动态链接库的形式存在。
  * 前端：就是输入法内核和输入法平台交互的界面 (wrapper)，它把后端包装起来，让 ibus, xim, macos 等平台能使用 SunPinyin 输入法。它一般提供一些快捷键，用户界面，和配置的功能。
  * 语言模型：语言模型是一些数据文件，其中包含我们熟悉的词库等数据。语言模型会在编译时下载。

在 GNU/Linux 平台上，前端目前支持 ibus 和 xim。您需要安装SunPinyin输入法后端之后才能安装前端。

## 输入法引擎的安装方法 ##

编译输入法引擎可以在代码根目录输入

```
scons
```

默认情况下的prefix是/usr/local。当然您也可以指定安装prefix。

```
scons --prefix=/usr
```

编译成功后可以使用
```
scons install
```

~~如果你之前指定过了prefix，那么这里install的时候一定要用相同的prefix，否则将使用默认prefix安装！~~

Note:
如果你有特殊的需求希望安装在特殊路径，可以使用`--install-sandbox=<dir>`选项。这不会改变prefix，只是换了一个拷贝目录而已，这个选项对打包很有用。

你可以使用pkg-config sunpinyin-2.0 --modversion来查看是否安装成功。

删除可以用：
```
scons -c install
```

## ibus界面（ibus-sunpinyin）的安装方法 ##

你需要先安装输入法引擎，确定你安装好输入法引擎后可以使用

```
cd wrapper/ibus
scons --prefix=/usr
sudo scons install
```

对于ibus，建议安装到/usr prefix，主要是因为怕ibus无法加载ibus-sunpinyin。

重启ibus来查看是否安装成功。

## xim界面（xsunpinyin）的安装方法 ##

你需要先安装输入法引擎，确定你安装好输入法引擎后可以使用

```
cd wrapper/xim
scons
sudo scons install
```

可以运行xsunpinyin来看看有没有输出错误。可以使用xsunpinyin -d 来以daemon模式启动，然而还是推荐你使用发行版的配置方法来自行配置xsunpinyin。对于debian/ubuntu在使用的imswitch，xsunpinyin已经提供了一个配置模版，在wrapper/xim/imswitch/xsunpinyin目录下，仅供参考。

## 系统词库安装方法 ##

从 https://code.google.com/p/open-gram/downloads 获得`lm_sc.3gm.arpa.tar.bz2`和`dict.utf8.tar.bz2`两个文件，将其解压到某个临时目录，并在同一个目录下执行以下命令：

```
# 复制词库安装所使用的 Makefile。
cp $PREFIX/share/doc/sunpinyin/SLM-inst.mk Makefile
# 生成词库文件。
make
# 安装词库文件（需要管理员权限）。
make install
```
