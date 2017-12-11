# 颜色{#Colors}

这些颜色的十六进制值可以在JavaScript中访问。该模块的全局版本公开了`Blueprint.Colors`对象。 在CommonJS中，您可以`import { Colors } from "@blueprintjs/core"`。

## 灰度{#Gray-scale}

黑色，白色之间的一切。灰度应该用于主UI框架：containers, headers, sections, boxes, etc.如果您需要引起对特定元素（按钮，图标，工具提示等）的注意，请使用其中一种[核心颜色](#colors.core-colors)。

@reactDocs GrayscalePalette

## 核心颜色{#Core-colors}

核心颜色保留用于用户界面设计。 使用这些来帮助引起对特定UI元素的注意，如按钮，标注，图标等。每个核心颜色被映射到我们称之为__visual intent__的地方。我们使用意图来传达UI元素的状态：

- _Blue_ (intent: primary) 从典型的灰度UI框架中提升元素。
- _Green_ (intent: success) 表示成功的操作。
- _Orange_ (intent: warning) 表示警告和中间状态。
- _Red_ (intent: danger) 表示错误和潜在的破坏性操作。

核心颜色也被设计为：

- 在任何应用程序中相处融洽，彼此并用。
- 遵守[WCAG 2.0](https://www.w3.org/TR/WCAG20/)标准，因此对视障人士和色盲用户来说非常方便。

@reactDocs CoreColorsPalette

## 扩展颜色{#Extended-colors}

扩展颜色通常应该保留用于数据可视化：任何时候您需要表示某种数据时，都可以使用这些颜色。这些颜色对于[WCAG 2.0](https://www.w3.org/TR/WCAG20/)辅助功能标准的要求不那么严格，因此不应该用于典型的用户界面设计 — 而应该考虑使用[核心颜色](#colors.core-colors)。

@reactDocs ExtendedColorsPalette

## 配色方案{#Color-schemes}

Use the following color scheme generators to produce color schemes for your data visualizations.
First, choose the kind of scheme based on the type of your data, then customize the number of values
using the forms below. Finally, copy the colors array into your application and make it live!

The following schemes have been carefully crafted to be visually striking and easily understandable
while remaining accessible to visually impaired and color blind users.

@### Sequential color schemes

Sequential color schemes imply order and are best suited for representing data that
ranges from low-to-high values either on an ordinal or on a numerical scale.

@reactDocs SequentialSchemePalette

@### Diverging color schemes

Diverging color schemes put equal emphasis on mid-range values and extremes
at both ends of the data range.

@reactDocs DivergingSchemePalette

@### Qualitative color schemes

Qualitative color schemes use a series of unrelated colors to create a
scheme that does not imply order, merely difference in kind.

@reactDocs QualitativeSchemePalette

@include color-aliases
