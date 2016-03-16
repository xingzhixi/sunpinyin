# Introduction #

这个文档介绍了SunPinyin未来Release的一些TODO。这些事情还需要解决，此后这些新特性可能会在未来的release中发布(2.5或者3.0)

# IME-Core #

## ~~作为动态链接库打包。~~ ##


## 加入扩展层 ##

使得sunpinyin能够使用python和C进行扩展。我们需要完成一下几个任务

  * view的实例化需要有机制管理。

> 考虑到扩展可以将任何一个view(CIMIClassicView)保存，而进行修改。如果保存一个指针的话，某些multi-view的wrapper(ibus)可能一段时间后会free这个view。所以应该有一个机制防止插件掉用已经free的view来进行修改。

  * 提供一个ffi友好的接口

> 小case，仅仅提供一个C wrapper而已。

  * 实现脚本语言wrapper

> 为脚本语言写个wrapper方便大家写扩展。

> 实现的原理就是dlsym查找ime-core已经导出的symbol。python中可以用ctype来实现。但是需要注意的是，由于历史原因MacOSX上依旧是静态链接，所以不能够依赖libsunpinyin.so，而是需要打开自身。(dlsym(NULL, func\_name);)


# ibus前端 #

## 维护和打包 ##

由于ibus变动比较频繁，而且ibus前段的维护者tchaikov也比较忙，所以需要更多的人参与测试、bug修复和打包。

# xim前端 #

## 皮肤支持 ##

提供类似sougou拼音的皮肤支持。能够简单的对原有的sougou皮肤进行修改即可使用。

# MacOSX前端 #

TBD