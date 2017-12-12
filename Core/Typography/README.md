# 排版{#Typography}

### 用法{#Usage}

在构建应用程序时请记住这些一般的网页排版准则。

- 所有组件的默认文本颜色均符合建议的[WCAG 2.0](https://www.w3.org/TR/WCAG20/)最低对比度。
- 如果您选择自定义文字颜色，请确保背后的背景提供适当的对比度。
- 尽量不要为您的字体大小或行高CSS规则显式地编写像素值。而是引用我们在Blueprint（`.pt-ui-text`，`$pt-font-size-large`等等）中提供的类和变量。

### 字体{#Fonts}

Blueprint不包含任何自己的字体;它将使用默认的sans-serif操作系统字体。我们提供一个类来使用默认的等宽字体。


@css fonts

### 标题{#Headings}

@css headings

### UI文本{#UI-text}

Blueprint Web应用程序的基本字体大小为14px。这应该是大多数不是标题或标题的短文本字符串的默认类型大小。如果您希望将某个元素的字体大小和行高重置为默认的基本样式，请使用`.pt-ui-text`类。对于长时间运行的文本，请参阅[运行文本样式](#core/typography.running-text)。

@css pt-ui-text

### 运行文本{#Running-text}

Longform text（如渲染的Markdown文档）受益于额外的间距和稍大的字体大小。 将`.pt-running-text`应用于父元素以调整以下元素的间距：

- `<p>` 标签增加了行高和字体大小。
- `<h*>`标签margin被调整，以在文档中的section之间提供清晰的分隔。
- `<ul>` and `<ol>` tags receive [`.pt-list`](#core/typography.lists) styles for legibility.
- `<ul>`和`<ol>`标签接收[`.pt-list`](#core/typography.lists)样式以便易读。

@css pt-running-text

### 链接{#Links}

通常只需使用一个`<a href="">`标签。 Blueprint样式不需要任何类。只有在悬停时链接才加下划线。

在链接中放置一个图标将导致它继承链接的文本颜色。

### 预先格式化的文本{#Preformatted-text}

对于代码块使用`<pre>`，对于内联代码使用`<code>`。请注意`<pre>`块会保留_所有_空格，所以你必须相应地格式化内容。

@css preformatted

### 块级引用{#Block-quotes}

块级引用被视为正在运行的文本。

@css blockquote

### 列表{#Lists}

Blueprint为列表元素提供了少量的全局样式和一些修饰符类。

`.pt-running-text`修饰符类中的`<ul>`和`<ol>`元素将自动采用`.pt-list`样式来提高可性。

@css lists

### 文本工具{#Text-utilities}

Blueprint提供了一小部分基于类的文本工具，可以应用于任何包含文本的元素。

@css utilities

### 国际化{#Internationalization}

在Blueprint中的I18n很简单。React组件公开用于定制任何字符串的属性;使用您选择的库来管理国际化的字符串。

#### 从右到左的文本{#Right-to-left-text}

使用实用程序类`.pt-rtl`。

@css pt-rtl

### 暗色主题{#Dark-theme}

Blueprint提供了两个UI颜色主题：明暗。亮色主题是默认激活的。暗色主题可以通过将类`pt-dark`添加到容器元素来应用所有嵌套元素。

一旦应用，暗色主题将层叠到`.pt-dark`容器内嵌套的`.pt-*`元素。没有办法在暗色容器中嵌套以亮色为主题的元素。

大多数元素只有在嵌入`.pt-dark`容器时才支持暗色主题，因为将单个元素标记为暗色是没有意义的。暗色容器因此负责设置暗的背景颜色。

以下元素和组件直接支持`.pt-dark`类（即`.pt-app.pt-dark`），并且可以用作嵌套的暗色子容器：

- `.pt-app`
- `.pt-card`
- Overlays: `Dialog`, `Popover`, `Tooltip`, `Toast`
- 当他们的触发在`.pt-dark`容器内时`Popover`和`Tooltip`会自动检测并为自己添加相同的类。

本文档站点不是直接显示深色组件，而是在页面右上角提供site-wide切换，以启用黑暗的主题。 在阅读文档时尝试一下。
