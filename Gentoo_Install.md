首先，从gentoo-china中安装ibus

然后，下载，把这个包解压到自己机器overlays的app-i18n下面。

emerge -av app-i18n/ibus-sunpinyin

完成后，重起ibus，在设置界面的输入法中添加sunpinyin，开始体验吧！

另外，由于sandbox环境，抓代码可能会遇到权限问题，解决办法是用root抓一下代码，记住ssh的授权即可。

```
# mkdir -p /usr/portage/distfiles/hg-src/ibus-sunpinyin
# cd /usr/portage/distfiles/hg-src/ibus-sunpinyin
# hg clone ssh://anon@hg.opensolaris.org/hg/nv-g11n/inputmethod inputmethod
```

目前，ibus-sunpinyin使用的是sunpinyin2的最新快照，功能不断更新中。