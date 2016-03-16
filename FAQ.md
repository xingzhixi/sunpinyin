# SunPinyin #
  1. SunPinyin的历史
    * SunPinyin是由Sun中国工程研究院的北京国际化中心开发，并贡献给开源社区的。
    * 最初由张磊（Phill.Zhang）博士独立完成，后来由众多的社区开发者共同推进，目前的版本是2.0.x。
  1. 它有什么好的？
    * 支持整句输入，能够记录用户的词汇和语言模型，从而训练出更适合你的输入法。
    * 它还在开发当中。
  1. 它有什么缺点？
    * 词表和语言模型都很老了，没有更新。但是我们正在想办法解决这个问题。（见 [project plan](http://wikis.sun.com/display/g11nhome/SunPinyin-2.0+Project+Plan+and+Status+Tracking)）
    * 还不支持繁体.
  1. 它不是什么
    * 它不是五笔输入法。SunPinyin，正如其名，是个拼音输入法。换句话说，我们不支持其他的输入形式，比如五笔。
    * 它不是输入法平台。SunPinyin 只有移植到输入法平台上才能使用。SunPinyin 2.0 目前支持 ibus, xim和Mac OS。

# 打包 #
  1. lm\_sc.3gm / lm\_sc.3gm.arpa.tar.bz2 怎么这么大？干什么用的？
    * 这是 tri-gram 的数据文件，这对 sunpinyin 很重要，可以说是 SLM (统计语言模型) 的核心，而 SLM 就是我们整句输入所采用的算法。lm\_sc.3gm 就是 language model simplified chinese, 3-gram 的缩写，它是 arpa 文件的二进制压缩格式。
    * 而 dict.utf8 则是我们的词表。
    * 两者都以文本形式发布，在编译时转换为二进制。
    * 将来我们计划把数据文件和程序分开发布。

# 安装 #
  1. 用 `sudo make install` 安装出现权限问题
    * 建议用 `su -c 'make install'` 安装
  1. 你们最新的源代码到底在哪里啊？这里只有一些打包文件。
    * 参见[Repositories](Repositories.md)

# 使用 #
  1. 为何SunPinyin在MacOS上无法输入汉字？
> > 确保您在执行安装程序时，安装了所需的数据文件。
> > > ![http://yongsun.me/wp-content/uploads/2010/03/sunpinyin-2.0-mac-installation-note.png](http://yongsun.me/wp-content/uploads/2010/03/sunpinyin-2.0-mac-installation-note.png)
  1. 从老版本 ibus-sunpinyin 升级到新版本，发现设置面板不能激活，直接运行/usr/lib/ibus-sunpinyin/ibus-setup-sunpinyin 得到如下错误：
```
/usr/lib/python2.6/site-packages/dbus/connection.py:242:
DeprecationWarning: object.__init__() takes no parameters
  super(Connection, self).__init__(*args, **kwargs)
Traceback (most recent call last):
  File "/usr/share/ibus-sunpinyin/setup/main.py", line 576, in <module>
    MainWindow().run()
  File "/usr/share/ibus-sunpinyin/setup/main.py", line 449, in run
    self.__read_config()
  File "/usr/share/ibus-sunpinyin/setup/main.py", line 514, in __read_config
    opt.init_ui()
  File "/usr/share/ibus-sunpinyin/setup/main.py", line 96, in init_ui
    self.read_config()
  File "/usr/share/ibus-sunpinyin/setup/main.py", line 160, in read_config
    self.widget.set_active(active)
TypeError: an integer is required
```
    * 这是因为新版本修改过 gconf 配置中用的数据类型，可以试一下把 `$HOME/.gconf/desktop/ibus/engine/SunPinyin/` 移开，然后重新启动 gconfd:
```
$ gconftool-2 --shutdown
```
  1. 怎么搞的，装上了输入法但是不能运行？
    1. 因为 ibus-sunpinyin 还在开发之中，所以你的问题很可能已经在开发版本中修复了。所以首先请确定你使用的是最新的版本.
    1. 因为 ibus-sunpinyin 在启动的时候会尝试在`$HOME/.ibus/sunpinyin`里读取或创建用户数据文件。所以请确保这个目录是可访问的。虽然 ibus-sunpinpinyin 会创建这个目录，但是如果有权限方面的限制，我们也没有办法越雷池一步。
    1. 如果你用的是最新版本，权限也没有问题。那么恭喜你，这是非常可能是一个 bug。你可以提交一个 bug report。
  1. 怎么提交 bug report
    1. 首先我们需要知道你使用 ibus-sunpinyin 的版本，比如 rc2，或者 hg:463。如果你不大清楚，也告诉我你是怎么安装的。
    1. 还有你操作系统的版本，比如我的是 Debian sid，昨天才更新过。
    1. 帮助我们收集一些其它信息会更有助于诊断问题：
      1. 先手动退出 ibus (右键点击系统状态栏中的输入法图标，选择退出)。
      1. 然后在虚拟终端窗口中输入
```
$ ibus-daemon --xim -v &
```
> > > 这样，程序就会把一些错误日志打印在终端上：
```
(process:4049): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed
/usr/share/ibus/ui/gtk/candidatepanel.py:194: DeprecationWarning: Use the new widget gtk.Tooltip
  self.__tooltips = gtk.Tooltips()
/usr/share/ibus/ui/gtk/candidatepanel.py:244: DeprecationWarning: Use the new widget gtk.Tooltip
  self.__tooltips.set_tip(self.__aux_label, "Aux string")
/usr/share/ibus/ui/gtk/candidatepanel.py:263: DeprecationWarning: Use the new widget gtk.Tooltip
  self.__tooltips.set_tip(self.__prev_button, "Previous page")
/usr/share/ibus/ui/gtk/candidatepanel.py:268: DeprecationWarning: Use the new widget gtk.Tooltip
  self.__tooltips.set_tip(self.__next_button, "Next page")
fopen bi-gram: Permission denied

(ibus-engine-sunpinyin:4054): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
fopen bi-gram: Permission denied
```
> > > 如果把这些错误信息和其他信息一起贴到 issue 里面，将会对我们有很大的帮助。