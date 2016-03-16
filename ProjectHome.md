SunPinyin is a statistical language model based Chinese input method, which was firstly developed by Sun Beijing Globalization team, and opensource'd to community with [opensolaris](http://opensolaris.org) project, with [LGPLv2](http://www.gnu.org/licenses/lgpl-2.1.html) and [CDDL](http://www.sun.com/cddl/cddl.html) dual-licenses.

SunPinyin had been ported to various input method platforms and operating systems. The 2.0 release currently supports iBus, XIM, and Mac OS X.

# News: #

### Notes to packagers of 2.0.3 ###

If you're trying to set an LDFLAGS or any other build flags, make sure it's correct!  There is a minor issue when dealing with external flags when they're incorrect.

Or you can apply [this patch](http://code.google.com/p/sunpinyin/downloads/detail?name=force-switch-updated.patch) to the build script.

### SunPinyin 2.0.3 Released ###

2.0.3 release is containing a lot of major fix compare to last release.  User should update to this release as soon as possible.  It fixed many inconveniet bugs.  Changes compare to 2.0.2 are described below:

Build:
  * CFLAGS, CXXFLAGS and LDFLAGS are recongnized.
  * Scons scripts now will remember the configuration arguments in configure.conf.
  * Ported to ARMEL architecture.
  * Able to build on FreeBSD.

libsunpinyin:
  * New LOGO!
  * History cache focus more on recent commits.
  * Supports --libdir and --libdatadir as configuration arguments.
  * Hunpin support. (Contributed by Hanjie Xu)
  * Fixed weird behavior of history with a single character.
  * Fixed a potential issue for candidate ranking.

ibus-sunpinyin:
  * Supports --libdir, --datadir, --execdir as configuration arguments.
  * Alt+num key as the candidate delete key for ibus-sunpinyin.
  * Able to build on IBus-1.4

xsunpinyin:
  * Synchronized the version between xsunpinyin and libsunpinyin project.
  * Fixed startup crash with empty directory.
  * Fixed position problem on multi-screen.
  * Fixed crash on exit, which caused history information lost.
  * Refact UI system
  * Added skin support
  * Fixed text overbound when pinyin are too long.
  * Fixed ignorance of ShuangPin setting.
  * Fixed weird behavior of fast switch to english. ([Issue 213](https://code.google.com/p/sunpinyin/issues/detail?id=213)).

scim-sunpinyin:
  * Add legacy support for scim (Thanks to liangguo)

### FIT (Fun Input Toy)和SunPinyin展开全面合作 ###

![http://yongsun.me/wp-content/uploads/2010/09/fit_and_sunpy_240x144.jpg](http://yongsun.me/wp-content/uploads/2010/09/fit_and_sunpy_240x144.jpg)

FIT和SunPinyin社区决定长期合作，联手制作下一个版本的FIT中文输入法。在合作中，FIT将使用SunPinyin的核心组件作为FIT的拼音输入引擎，完全替换掉旧版的fitx拼音引擎。新的拼音引擎将应用在FIT的Mac版、iPhone版和即将推出的iPad版。


对SunPinyin社区来说，SunPinyin的Mac版本将不会作为社区的工作重心，从而将更多的将精力集中到引擎、算法本身的改进中去，并全力协同FIT整合sunpinyin的输入引擎。FIT团队也会积极参与到引擎的改进和完善中，并将会负责SunPinyin-for-Mac的用户支持工作。SunPinyin-for-Mac依然遵循CDDL+LGPLv2.1，合作并不会妨碍任何有兴趣改进/完善它的朋友，贡献自己的努力。


另见[FIT官方网站的声明](http://fit4.cn/blog?bid=302)。

