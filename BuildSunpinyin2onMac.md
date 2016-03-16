1. 安装scons

下载http://prdownloads.sourceforge.net/scons/scons-1.3.1.tar.gz，并将其解压，

```
$ cd scons-1.3.1
$ python setup.py install
```

2. 从github上clone/pull最新的sunpinyin源代码

```
$ git clone git://github.com/sunpinyin/sunpinyin.git
```

3. 使用scons来构建sunpinyin的工具及数据文件

```
$ cd sunpinyin
$ scons
```

5. 最后就是build基于IMKit的输入法前端了，

```
$ cd wrapper/macos
$ make clean; make
$ sudo make install
```

现在，sunpinyin-2.0应该已经安装到系统中了，需要re-login才可以看到这个输入法。