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

Simply use an `<a href="">` tag as you normally would. No class is necessary for Blueprint styles.
Links are underlined only when hovered.

Putting an icon inside a link will cause it to inherit the link's text color.

@## Preformatted text

Use `<pre>` for code blocks, and `<code>` for inline code. Note that `<pre>` blocks will
retain _all_ whitespace so you'll have to format the content accordingly.

@css preformatted

@## Block quotes

Block quotes are treated as running text.

@css blockquote

@## Lists

Blueprint provides a small amount of global styling and a few modifier classes for list elements.

`<ul>` and `<ol>` elements in blocks with the `.pt-running-text` modifier class will
automatically assume the `.pt-list` styles to promote readability.

@css lists

@## Text utilities

Blueprint provides a small handful of class-based text utilities which can applied to any element
that contains text.

@css utilities

@## Internationalization

I18n in Blueprint is straightforward. React components expose props for customizing any strings;
use the library of your choice for managing internationalized strings.

@### Right-to-left text

Use the utility class `.pt-rtl`.

@css pt-rtl

@## Dark theme

Blueprint provides two UI color themes: light and dark. The light theme is active by default. The
dark theme can be applied by adding the class `pt-dark` to a container element to theme all nested
elements.

Once applied, the dark theme will cascade to nested `.pt-*` elements inside a `.pt-dark` container.
There is no way to nest light-themed elements inside a dark container.

Most elements only support the dark theme when nested inside a `.pt-dark` container because it does
not make sense to mark individual elements as dark. The dark container is therefore responsible for
setting a dark background color.

The following elements and components support the `.pt-dark` class directly (i.e, `.pt-app.pt-dark`)
and can be used as a container for nested dark children:

- `.pt-app`
- `.pt-card`
- Overlays: `Dialog`, `Popover`, `Tooltip`, `Toast`
- `Popover` and `Tooltip` will automatically detect when their trigger is inside a `.pt-dark`
container and add the same class to themselves.

Rather than illustrating dark components inline, this documentation site provides a site-wide switch
in the top right corner of the page to enable the dark theme. Try it out as you read the docs.
