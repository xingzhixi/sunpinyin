# Introduction #

当deb包无法使用时，用户需要手动配置xsunpinyin。这个过程需要用户有一些shell脚本的基础知识。所以，我们强烈建议普通用户采用发行版发行的安装包，如deb包，rpm包或者gentoo的ebuild。

# 运行要求 #

xsunpinyin需要用户有一个unicode的locale。具体的说要utf8。（据说gbk也可以正常trigger，但是作为现代`*`nix用户，utf8应该是比较明智的选择）

# 编译安装 #

首先你需要自行编译安装，你需要autotools(autoconf, automake, gettext等常见包)。同时为了编译xsunpinyin你还需要xlib和gtk的dev包。安装好这些包以后我们就可以解压了。
```
tar xvf sunpinyin-2.0.tar.gz
cd sunpinyin-2.0
./configure
make
cd wrapper/xim
make
sudo make install
```

这样将会编译，安装xsunpinyin。安装好之后你可以试图启动设置程序
```
xsunpinyin-preferences
```
来检查是否安装成功。

# 设置 #

xsunpinyin只需要一个环境变量即可工作－XMODIFIER。为了我们能在gtk/qt中默认使用xim输入法我们可以设置一下变量

```
export XMODIFIERS="@im=xsunpinyin"
export GTK_IM_MODULE=xim
export QT_IM_MODULE=xim
```

然后启动xsunpinyin即可使用。或者可以xsunpinyin -d启动daemon，当前的shell就可以安全退出了。

这些环境变量强烈推荐你写成一个脚本放到/etc/X11/Xsession.d下，这样xsunpinyin就可以在整个xsession中使用了。