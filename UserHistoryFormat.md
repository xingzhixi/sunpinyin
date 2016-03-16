#用户历史数据文件的格式

# 用户历史数据 #

用户历史数据是用来保存用户的输入数据。文件名一般是 `$USER_DIR/history` 。每次用户选词，并且提交选中的词之后，都会保存用户词库和用户的历史数据。

# 格式 #

它含有多条 bi-gram 序列，序列间，以 DCWID (Don't Care Word ID) 分隔。DCWID 的值是 0xffff。
每个 bi-gram 序列含有多个 bi-gram。这些 bi-gram 序列的形式如下：

> wid\_1 wid\_2 wid\_3

这个 bi-gram 序列表示了三个 bi-gram，即
  1. NCWID, wid\_1
  1. wid\_1, wid\_2
  1. wid\_2, wid\_3
word id 以 32 位的 big-endian 整数表示。`history` 最多保存 8192 个 wid ，即其大小最大为 32768 字节。