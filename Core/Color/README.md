# 颜色{#Colors}

这些颜色的十六进制值可以在JavaScript中访问。该模块的全局版本公开了`Blueprint.Colors`对象。 在CommonJS中，您可以`import { Colors } from "@blueprintjs/core"`。

### 灰度{#Gray-scale}

黑色，白色之间的一切。灰度应该用于主UI框架：containers, headers, sections, boxes, etc.如果您需要引起对特定元素（按钮，图标，工具提示等）的注意，请使用其中一种[核心颜色](#colors.core-colors)。

@reactDocs GrayscalePalette

### 核心颜色{#Core-colors}

核心颜色保留用于用户界面设计。 使用这些来帮助引起对特定UI元素的注意，如按钮，标注，图标等。每个核心颜色被映射到我们称之为__visual intent__的地方。我们使用意图来传达UI元素的状态：

- _Blue_ (intent: primary) 从典型的灰度UI框架中提升元素。
- _Green_ (intent: success) 表示成功的操作。
- _Orange_ (intent: warning) 表示警告和中间状态。
- _Red_ (intent: danger) 表示错误和潜在的破坏性操作。

核心颜色也被设计为：

- 在任何应用程序中相处融洽，彼此并用。
- 遵守[WCAG 2.0](https://www.w3.org/TR/WCAG20/)标准，因此对视障人士和色盲用户来说非常方便。

@reactDocs CoreColorsPalette

### 扩展颜色{#Extended-colors}

扩展颜色通常应该保留用于数据可视化：任何时候您需要表示某种数据时，都可以使用这些颜色。这些颜色对于[WCAG 2.0](https://www.w3.org/TR/WCAG20/)辅助功能标准的要求不那么严格，因此不应该用于典型的用户界面设计 — 而应该考虑使用[核心颜色](#colors.core-colors)。

@reactDocs ExtendedColorsPalette

### 配色方案{#Color-schemes}

使用以下配色方案生成器为您的数据可视化生成配色方案。首先，根据您的数据类型选择方案类型，然后使用下面的表单自定义数值。最后，将颜色数组复制到您的应用程序中并使其生效！

以下方案经过精心打造，视觉震撼，易于理解，同时视障人士和色盲用户仍可使用。

#### 顺序配色方案{#Sequential-color-schemes}

顺序颜色方案意味着顺序，并且最适合用于表示在序数或数字尺度上从低到高值的数据。

@reactDocs SequentialSchemePalette

#### 发散的配色方案{#Diverging-color-schemes}

分散的配色方案同时强调数据范围两端的中间值和极端值。

@reactDocs DivergingSchemePalette

#### 定性配色方案{#Qualitative-color-schemes}

定性的配色方案使用一系列不相关的颜色来创建一个不包含顺序的方案，仅仅是种类上的差异。

@reactDocs QualitativeSchemePalette

### 颜色别名{#Color-aliases}

这些变量是我们[颜色](#colors)的语义别名。 它们在整个Blueprint中使用，以确保各个组件之间的颜色使用一致。

<table class="pt-table docs-color-aliases-table">
    <thead>
        <tr>
            <th></th>
            <th>Variable</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
                <div class="docs-color-bubble alias-intent-primary"></div>
            </td>
            <td><code>$pt-intent-primary</code></td>
            <td>Primary intent color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-intent-success"></div>
            </td>
            <td><code>$pt-intent-success</code></td>
            <td>Success intent color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-intent-warning"></div>
            </td>
            <td><code>$pt-intent-warning</code></td>
            <td>Warning intent color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-intent-danger"></div>
            </td>
            <td><code>$pt-intent-danger</code></td>
            <td>Danger intent color</td>
        </tr>
        <!---->
        <tr>
            <td>
                <div class="docs-color-bubble alias-app-background-color"></div>
            </td>
            <td><code>$pt-app-background-color</code></td>
            <td>Application background color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-app-background-color"></div>
            </td>
            <td><code>$pt-dark-app-background-color</code></td>
            <td>Dark theme application background color</td>
        </tr>
        <!---->
        <tr>
            <td>
                <div class="docs-color-bubble alias-text-color"></div>
            </td>
            <td><code>$pt-text-color</code></td>
            <td>Default text color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-text-color-muted"></div>
            </td>
            <td><code>$pt-text-color-muted</code></td>
            <td>Muted text color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-text-color-disabled"></div>
            </td>
            <td><code>$pt-text-color-disabled</code></td>
            <td>Disabled text color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-heading-color"></div>
            </td>
            <td><code>$pt-heading-color</code></td>
            <td>Text color for headers</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-link-color"></div>
            </td>
            <td><code>$pt-link-color</code></td>
            <td>Text color for links</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-text-color"></div>
            </td>
            <td><code>$pt-dark-text-color</code></td>
            <td>Dark theme default text color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-text-color-muted"></div>
            </td>
            <td><code>$pt-dark-text-color-muted</code></td>
            <td>Dark theme muted text color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-text-color-disabled"></div>
            </td>
            <td><code>$pt-dark-text-color-disabled</code></td>
            <td>Dark theme disabled text color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-heading-color"></div>
            </td>
            <td><code>$pt-dark-heading-color</code></td>
            <td>Dark theme text color for headers</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-link-color"></div>
            </td>
            <td><code>$pt-dark-link-color</code></td>
            <td>Dark theme text color for links</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-text-selection-color"></div>
            </td>
            <td><code>$pt-text-selection-color</code></td>
            <td>Text selection color</td>
        </tr>
        <!---->
        <tr>
            <td>
                <div class="docs-color-bubble alias-icon-color"></div>
            </td>
            <td><code>$pt-icon-color</code></td>
            <td>Default icon color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-icon-color-hover"></div>
            </td>
            <td><code>$pt-icon-color-hover</code></td>
            <td>Hovered icon color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-icon-color-disabled"></div>
            </td>
            <td><code>$pt-icon-color-disabled</code></td>
            <td>Disabled icon color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-icon-color-selected"></div>
            </td>
            <td><code>$pt-icon-color-selected</code></td>
            <td>Selected icon color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-icon-color"></div>
            </td>
            <td><code>$pt-dark-icon-color</code></td>
            <td>Dark theme default icon color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-icon-color-hover"></div>
            </td>
            <td><code>$pt-dark-icon-color-hover</code></td>
            <td>Dark theme hovered icon color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-icon-color-disabled"></div>
            </td>
            <td><code>$pt-dark-icon-color-disabled</code></td>
            <td>Dark theme disabled icon color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-icon-color-selected"></div>
            </td>
            <td><code>$pt-dark-icon-color-selected</code></td>
            <td>Dark theme selected icon color</td>
        </tr>
        <!---->
        <tr>
            <td>
                <div class="docs-color-bubble alias-divider-black"></div>
            </td>
            <td><code>$pt-divider-black</code></td>
            <td>Black divider color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-divider-black"></div>
            </td>
            <td><code>$pt-dark-divider-black</code></td>
            <td>Dark theme black divider color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-divider-white"></div>
            </td>
            <td><code>$pt-dark-divider-white</code></td>
            <td>Dark theme white divider color</td>
        </tr>
        <!---->
        <tr>
            <td>
                <div class="docs-color-bubble alias-code-text-color"></div>
            </td>
            <td><code>$pt-code-text-color</code></td>
            <td>Code text color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-code-background-color"></div>
            </td>
            <td><code>$pt-code-background-color</code></td>
            <td>Code background color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-code-text-color"></div>
            </td>
            <td><code>$pt-dark-code-text-color</code></td>
            <td>Dark theme code text color</td>
        </tr>
        <tr>
            <td>
                <div class="docs-color-bubble alias-dark-code-background-color"></div>
            </td>
            <td><code>$pt-dark-code-background-color</code></td>
            <td>Dark theme code background color</td>
        </tr>
    </tbody>
