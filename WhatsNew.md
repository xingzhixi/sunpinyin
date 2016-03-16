# What's New #
  * 支持双拼输入，实现了五种常用的双拼方案，MS2003，紫光，ABC,自然码，pinyin++。
  * 除了 bi-gram 语言模型，现在还能保存用户词库(支持用户dict)。
  * 支持模糊拼音和纠错
  * 支持用户自定义字符映射，也就是说可以在中文输入模式下，输入给定英文标点，能输出用户指定的字符串

# What's New #
  * Implement Double Pinyin support, Five shunpin plans:
> > MS2003, ZiGuang, ABC, Ziranma, pinyin++
  * Add user dictionary support.
  * Add support for fuzzy pinyin
  * Add support for auto-correct pinyin
  * Add Support for customize character mapping.
  * Implement wrapper for ibus framework
> > (include the user preferences GUI; i18n support: en\_US and zh\_CN PO files.)
  * Implement wrapper for XIM framework