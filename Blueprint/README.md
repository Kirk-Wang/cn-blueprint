## Blueprint{#Blueprint}

Blueprint是一个针对web的，基于React的UI toolkit。
* 开发和问题跟踪产生在[github.com/palantir/blueprint](https://github.com/palantir/blueprint)。
* 发行版被标记并记录[在GitHub上](https://github.com/palantir/blueprint/releases)。
* 对于支持请求，在Stack Overflow上使用[__blueprintjs__标记](http://stackoverflow.com/questions/tagged/blueprintjs)。

#### 浏览器支持{#Browser-support}

**Blueprint支持Chrome、Firefox、Safari、IE 11和Microsoft Edge。**

* 在IE中，您可能会遇到降级的视觉效果。 
* IE 10及以下版本由于缺乏对CSS Flexbox Layout的支持而不被支持。 
* 这些浏览器在[2016年1月](https://www.microsoft.com/en-us/WindowsForBusiness/End-of-IE-support)被微软（支持结束）弃用。

#### 用法

Blueprint作为NPM包的集合在`@blueprintjs`作用域下。完整的包列表和它们的最新版本出现在上面的_发行版_下拉列表下。

每个包都包含一个CSS文件和一组暴露React组件的CommonJS模块。`main`模块从所有模块中导出所有symbols，所以你不必导入单个文件（尽管你可以如果你想）。JavaScript组件是稳定的，它们的API遵循[semantic versioning](http://semver.org/)。

#### NPM 安装

1. 使用NPM客户端（如`npm`或`yarn`）安装核心软件包，引入所有相关的依赖关系：

  ```sh
  npm install --save @blueprintjs/core
  ```

1. 如果你看到`UNMET PEER DEPENDENCY`错误，你应该手动安装React：

  ```sh
  npm install --save react react-dom react-addons-css-transition-group
  ```

1. 安装之后，您将能够在应用程序中导入React组件：

  ```tsx
  // 提取特定的组件
  import { Intent, Spinner, DatePickerFactory } from "@blueprintjs/core";
  // 或者提取一切！
  import * as Blueprint from "@blueprintjs/core";

  // 使用JSX：
  const mySpinner = <Spinner intent={Intent.PRIMARY} />;

  // 使用命名空间导入：
  const anotherSpinner = <Blueprint.Spinner intent={Blueprint.Intent.PRIMARY}/>;

  // 如果您不使用JSX，请使用React.createElement简写工厂。
  // 每个组件都提供相应的<Name>Factory.
  const myDatePicker = DatePickerFactory();
  ```

1. 不要忘记包含来自每个Blueprint包的主要CSS文件！另外，`resources/`目录包含支持的媒体，如字体和图片。

  ```html
  <!-- 在普通的旧的可靠的HTML -->
  <!DOCTYPE HTML>
  <html>
    <head>
      ...
      <!-- 手动包含依赖项 -->
      <link href="path/to/node_modules/normalize.css/normalize.css" rel="stylesheet" />
      <link href="path/to/node_modules/@blueprintjs/core/dist/blueprint.css" rel="stylesheet" />
      ...
    </head>
    ...
  </html>
  ```

  ```css.scss
  // 或者在CSS文件中使用 node-style 的包解析：
  //（依赖关系的样式表应该会被自动解析）
  @import "~@blueprintjs/core";
  ```

#### CDN 消费

Blueprint支持过去的[unpkg CDN](https://unpkg.com)。每个软件包提供一个UMD`dist/[name].bundle.js`文件，其中包含捆绑的源代码。UMD包装器在`Blueprint`全局变量上暴露了每个库：`Blueprint.Core`，`Blueprint.Datetime`等

这些包_不包括_外部依赖; 你的应用程序将需要确保`normalize.css`，`React`，`classnames`和`Tether`在运行时可用。

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>Blueprint Starter Kit</title>
    <link href="https://unpkg.com/normalize.css@^4.1.1" rel="stylesheet" />
    <link href="https://unpkg.com/@blueprintjs/core@^1.11.0/dist/blueprint.css" rel="stylesheet" />
  </head>
  <body>
    <script src="https://unpkg.com/classnames@^2.2"></script>
    <script src="https://unpkg.com/dom4@^1.8"></script>
    <script src="https://unpkg.com/tether@^1.4"></script>
    <script src="https://unpkg.com/react@^15.3.1/dist/react-with-addons.min.js"></script>
    <script src="https://unpkg.com/react-dom@^15.3.1/dist/react-dom.min.js"></script>
    <script src="https://unpkg.com/@blueprintjs/core@^1.11.0"></script>

    <div id="btn"></div>
    <script>
      const button = React.createElement(Blueprint.Core.Button, {
        iconName: "predictive-analysis",
        text: "CDN Blueprint is go!",
      });
      ReactDOM.render(button, document.querySelector("#btn"));
    </script>
  </body>
</html>
```

@### DOM4

Blueprint relies on a handful of DOM Level 4 API methods: `el.query`, `el.queryAll`, and
`el.closest()`. `@blueprintjs/core` depends on a [polyfill library called `dom4`][dom4] to ensure
these methods are available. This module is conditionally loaded if Blueprint is used in a browser
environment.

[dom4]: https://webreflection.github.io/dom4/

@### TypeScript

Blueprint is written in TypeScript and therefore its own `.d.ts` type definitions are distributed in
the NPM package and should be resolved automatically by the compiler. However, you'll need to
install typings for Blueprint's dependencies before you can consume it:

```sh
# required for all @blueprintjs packages:
npm install --save @types/pure-render-decorator @types/react @types/react-dom @types/react-addons-css-transition-group

# @blueprintjs/datetime requires:
npm install --save @types/moment

# @blueprintjs/table requires:
npm install --save @types/es6-shim
```

<div class="pt-callout pt-intent-primary pt-icon-info-sign">
  For more information, see the TypeScript Handbook for
  [guidance on consuming declaration files][handbook].
</div>

[handbook]: https://www.typescriptlang.org/docs/handbook/declaration-files/consumption.html

@### Vanilla JS APIs

JS components are built using React, but that does not limit their usage to just React applications.
You can render any component in any JavaScript application with `ReactDOM.render`. Think of it like
using a jQuery plugin.

```tsx
const myContainerElement = document.querySelector(".my-container");

// with JSX
ReactDOM.render(
    <Spinner className="pt-intent-primary pt-small" />,
    myContainerElement
);

// with vanilla JS, use the factory
ReactDOM.render(
    SpinnerFactory({
        className: "pt-intent-primary pt-small"
    }),
    myContainerElement
);
```

To remove the component from the DOM and clean up, unmount it:

```tsx
ReactDOM.unmountComponentAtNode(myContainerElement);
```

Check out the [React API docs](https://facebook.github.io/react/docs/react-api.html) for more details.


You'll need to install React `v15.x` or `v0.14.x` alongside Blueprint.

```sh
npm install --save @blueprintjs/core react react-dom react-addons-css-transition-group
```

Import components from the `@blueprintjs/core` module into your project.
Don't forget to include the main CSS stylesheet too!

**Review the [general usage docs](#blueprint.usage) for more complete installation instructions.**

@## Understanding TypeScript

Blueprint is written in [TypeScript](https://www.typescriptlang.org/), a statically typed superset
of JavaScript that compiles to plain JavaScript. All the code samples throughout this site and
all interactive examples are also written in TypeScript. TypeScript code looks exactly like ES2015+
code with the addition of type signatures, which typically appear after colons and are colored
gold in our syntax theme.

```ts
// variables
const variableName: varType;
const name: string;
const disabled: boolean;

// functions (and function variables)
function funcName(arg1: argType, arg2: argType): returnType { }
const funcName: (arg1: argType) => returnType;
function split(str: string, delim: string): string[] { }
function map<T, U>(array: T[], iterator: (item: T, index: number) => U): U[];

// interfaces describe plain objects
// (we use the convention that interfaces begin with "I")
interface IOption {
  label: string;
  value: string;
}
const option: IOption = { label: "Name", value: "gilad" };
```

**You do not need to use TypeScript to consume Blueprint** (but major "props" if you do). Familiarity
with the syntax is suggested so you can follow our examples
([the handbook](https://www.typescriptlang.org/docs/handbook/basic-types.html) has good documentation
for getting started). Simply ignoring the type annotations in your head will produce valid ES2015 code.

@## Development & contributions

Most dev-related information is on [our GitHub wiki](https://github.com/palantir/blueprint/wiki),
including our [coding guidelines](https://github.com/palantir/blueprint/wiki/Coding-guidelines)
and our [development practices](https://github.com/palantir/blueprint/wiki/Development-Practices).