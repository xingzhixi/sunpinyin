# 界面设计 #

| **类别** | **配置项目** | **UI 元素** | **备注** |
|:-------|:---------|:----------|:-------|
| 键盘     | 翻页键      | check box | "-/=", ",/." |
| ^      | 全角半角切换   | check box | 待定     |
| ^      | 中英文标点切换  | check box | ctrl+. |
| 界面     | 候选词窗口的大小 | dropdown menu | 6-10   |
| 拼音     | 拼音方案     | radio button | 全拼, 双拼 |
| ^      | 双拼方案     | dropdown menu | 见 [双拼方案](configurations#Shuang-Pin_Schemes.md) |
| ^      | 模糊拼音     | check box | 见 [模糊拼音](configurations#Ambiguous_Pinyin.md) |
| ^      | 自动纠错     | check box | 见 [自动纠错](configurations#Auto_Correction.md) |
| ^      | 记忆强度     | dropdown menu | 1-10   |
| ^      | 用户辞典开关   | check box | 待定     |
| ^      | 自定义标点符号映射 | ??        | ??     |
| ^      | 字符集      | radio button | gb2312, gbk |

## Shuang-Pin Schemes ##
  * MS2003
  * ZiRanMa
  * ZiGuang
  * ABC
  * PinYinJiaJia

## Ambiguous Pinyin ##

如果启用“模糊拼音”，可选择启用那些模糊拼音对 （可多选 check box）
| "z" |  "zh" |
|:----|:------|
| "c" |  "ch" |
| "s" |  "sh" |
| "an" | "ang" |
| "on" | "ong" |
| "en" | "eng" |
| "in" | "ing" |
| "eng" | ong"  |
| "ian" | iang" |
| "uan" | uang" |
| "l" |  "n"  |
| "f" |  "h"  |
| "r" |  "l"  |
| "k" |  "g"  |

## Auto Correction ##

如果启用“自动纠错”，可选择启用那些拼音对 （可多选 check box）
| "ign" | "ing" |
|:------|:------|
| "img" | "ing" |
| "uei" | "ui"  |
| "uen" | "un"  |
| "iou" | "iu"  |