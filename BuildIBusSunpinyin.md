# 准备工作 #

除了 gcc, libtool, intltool 等基本的编译环境之外，编译 ibus-sunpinyin 还需要

  * libibus-dev
  * libsqlite3-dev
  * python 2.6

对Debian/Ubuntu的用户来说，可以通过下面的命令安装所需要的开发包，

```
$ sudo apt-get install build-essential libtool libibus-dev libsqlite3-dev intltool
```

# 编译安装 #

```
$ tar xvf sunpinyin-2.0.20091104.tar.gz
$ cd sunpinyin-2.0
$ ./configure --enable-ibus --disable-documents --prefix=/usr --libexecdir=/usr/lib/ibus-sunpinyin
$ make && su -c 'make install'
```

# build from git clone #

```
$ git clone git://github.com/sunpinyin/sunpinyin.git
$ cd sunpinyin
$ ./autogen.sh --enable-ibus --disable-documents --prefix=/usr --libexecdir=/usr/lib/ibus-sunpinyin
$ make && su -c 'make install'
```