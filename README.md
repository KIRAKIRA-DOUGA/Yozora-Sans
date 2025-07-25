# Yozora Sans

这是一个规范化标点符号的修正字形用黑体字体。\
其目的旨在修正各字体对 Unicode 及 OpenType 布局功能的支持不佳，导致标点符号等字形显示不美观的问题。

该字体基于 [Inter](https://github.com/rsms/inter)（西文字形部分）和[思源黑体](https://github.com/adobe-fonts/source-han-sans)（东亚字形部分）修改而成，使用和修改时请尊重这些字体的声明。

该字体是一个 woff2 可变字体，其字重变化范围为 250 ~ 900。

## 使用方法

该字体不含主要语言字母的字形，无法独立使用。需配合其它字体一起使用。

以 CSS 为例：

```css
font-family: "Yozora Sans", /* 其它字体声明，不得为空！ */;
```

CSS 内嵌字体声明：

```css
@font-face {
	font-family: "Yozora Sans";
	font-weight: 250 900;
	font-style: normal;
	src: url("assets/fonts/Yozora Sans/YozoraSans-VF.woff2") format("woff2");
	font-display: swap;
}
```

## 维护

该字体仅实现了目前所需的功能，没有实现所有可能的功能，后续将不断完善。\
并且没有进行过多的测试，可能会遇到 bug。

## 字形修改说明

### 标点挤压

具体包含：
1. **平替半宽 (halt)**
2. **间距调节 (kern)**

```
# 左括号
‘“〈《「『【〔〖〘〚（［｛｟

# 右括号
’”〉》」』】〕〗〙〛）］｝｠

# 点号
、。，．：；？！
```

1. 左括号类和右括号类将会替换为半宽形式，点号类不会。
2. 点号类与右括号类或点号类相连时，前面的点号类字形会被挤压掉右半边部分。

### 标点不间断连字 (liga)

1. 连用两个 M 宽长划（—, Em Dash），会替换为两倍 M 宽长划（⸺, Two-Em Dash）。
2. 连用三个 M 宽长划（—, Em Dash），会替换为三倍 M 宽长划（⸻, Three-Em Dash）。

其中，两倍 M 宽长划与三倍 M 宽长划均已调整宽度使其与两倍或三倍汉字的宽度相等。

### 中日韩本地化字形替换 (locl)

正常情况下，中线水平省略号（⋯）与 M 宽长划（—）均与西文字母高度平齐。

在中日韩语境下，它们将会与汉字高度平齐。

### 区分大小写的字形替换 (case)

正常情况下，颚化符（~）与小写字母高度平齐。

当其两边有大写字母或数字时，其将与大写字母高度平齐。

### 竖排字形替换 (vert)

调整了波形长划（〜）、全宽颚化符（～）、颚化符（~）在竖排文本下的字形，使其按照规范的方向扭曲（即先顺时针旋转 90 度之后，再水平翻转一次）。

### 全宽蝌蚪引号 (SVS)

[Unicode 16.0](https://www.unicode.org/versions/Unicode16.0.0/) 引入了基于 Unicode 标准化变体序列形式的全角单双引号。但截至该字体制作之前尚未有任何字体支持该变体序列。

字符 | Unicode | 名称
--- | --- | ---
“&#xfe00; | U+201C U+FE00 | 半宽左双引号
”&#xfe00; | U+201D U+FE00 | 半宽右双引号
‘&#xfe00; | U+2018 U+FE00 | 半宽左单引号
’&#xfe00; | U+2019 U+FE00 | 半宽右单引号
“&#xfe01; | U+201C U+FE01 | 全宽左双引号
”&#xfe01; | U+201D U+FE01 | 全宽右双引号
‘&#xfe01; | U+2018 U+FE01 | 全宽左单引号
’&#xfe01; | U+2019 U+FE01 | 全宽右单引号

它只对弯括号起作用，对直引号不起任何作用。

这需要字体支持，否则你将无法看出两者之间的区别。

该字体中仅包含全宽单双引号的字形，未包含半宽单双引号的字形。你需要搭配其它西文字体一起使用，并将该字体置于它们之前。

不然的话有一个问题，因为西文字体通常不在意全半宽，因此也通常不会支持 Unicode 变体序列。这导致了无论你是否书写了该变体序列，一旦你将西文字体置于字体堆栈的开头，一律将会显示为半宽引号。即便后续有字体支持该变体序列，也没机会显示到它。

## 协议

Yozora Sans 采用 [OFL 1.1 协议](https://openfontlicense.org/open-font-license-official-text/)。更多信息请参阅 LICENSE 文件。
