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

#### 用法{#Usage}

Blueprint作为NPM包的集合在`@blueprintjs`作用域下。完整的包列表和它们的最新版本出现在上面的_发行版_下拉列表下。

每个包都包含一个CSS文件和一组暴露React组件的CommonJS模块。`main`模块从所有模块中导出所有symbols，所以你不必导入单个文件（尽管你可以如果你想）。JavaScript组件是稳定的，它们的API遵循[semantic versioning](http://semver.org/)。

#### NPM 安装{#NPM-installation}

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

#### CDN 使用{#CDN-consumption}

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

#### DOM4{#DOM4}

Blueprint依赖少数DOM Level 4 API方法：`el.query`，`el.queryAll`和`el.closest()`。 `@blueprintjs/core`依赖于[名为`dom4`的polyfill库][dom4]，以确保这些方法可用。如果在浏览器环境中使用Blueprint，则该模块将被有条件加载。

[dom4]: https://webreflection.github.io/dom4/

#### TypeScript{#TypeScript}

Blueprint是用TypeScript编写的，因此它自己的`.d.ts`类型定义分布在NPM包中，并且应由编译器自动解析。但是，在你使用它之前，您需要为Blueprint的依赖项安装typings：

```sh
# required for all @blueprintjs packages:
npm install --save @types/pure-render-decorator @types/react @types/react-dom @types/react-addons-css-transition-group

# @blueprintjs/datetime requires:
npm install --save @types/moment

# @blueprintjs/table requires:
npm install --save @types/es6-shim
```

有关更多信息，请参阅TypeScript手册关于[使用定义文件指南][handbook]。

[handbook]: https://www.typescriptlang.org/docs/handbook/declaration-files/consumption.html

#### Vanilla JS APIs{#Vanilla-JS-APIs}

JS组件是使用React构建的，但并不仅限于React应用程序。您可以在任何JavaScript应用程序中使用`ReactDOM.render`渲染任何组件。把它想像成使用jQuery插件。

```tsx
const myContainerElement = document.querySelector(".my-container");

// 与 JSX
ReactDOM.render(
    <Spinner className="pt-intent-primary pt-small" />,
    myContainerElement
);

// 与 vanilla JS, 使用 factory
ReactDOM.render(
    SpinnerFactory({
        className: "pt-intent-primary pt-small"
    }),
    myContainerElement
);
```

要从DOM中删除组件并清理，请将其卸载：

```tsx
ReactDOM.unmountComponentAtNode(myContainerElement);
```

查看[React API文档](https://facebook.github.io/react/docs/react-api.html)了解更多详情。

你需要在Blueprint上安装React`v15.x`或`v0.14.x`。

```sh
npm install --save @blueprintjs/core react react-dom react-addons-css-transition-group
```

将组件从`@blueprintjs/core`模块导入到您的项目中。不要忘记也包括主CSS样式表！

**查看[一般用法文档](#blueprint.usage)以获取更完整的安装说明。**

#### 理解 TypeScript{#Understanding-TypeScript}

Blueprint是用[TypeScript](https://www.typescriptlang.org/)编写的，它是一个JavaScript静态类型的超集，可以编译成普通的JavaScript。本站点中的所有代码示例以及所有交互式示例也都是用TypeScript编写的。TypeScript代码看起来与ES2015+代码完全一样，但是添加了类型签名，通常在冒号后面出现，并在语法主题中显示为金色。

```ts
// 变量
const variableName: varType;
const name: string;
const disabled: boolean;

// 函数（和函数变量）
function funcName(arg1: argType, arg2: argType): returnType { }
const funcName: (arg1: argType) => returnType;
function split(str: string, delim: string): string[] { }
function map<T, U>(array: T[], iterator: (item: T, index: number) => U): U[];

// 接口描述普通对象
//（我们使用以“I”开头的接口约定）
interface IOption {
  label: string;
  value: string;
}
const option: IOption = { label: "Name", value: "gilad" };
```

**您并不需要使用TypeScript来消费Blueprint** (but major "props" if you do). 建议熟悉语法，以便您可以按照我们的示例进行操作（[该手册](https://www.typescriptlang.org/docs/handbook/basic-types.html)有很好的入门文档）。

#### 开发 & 贡献{#Development-contributions}

大多数与开发相关的信息都在[我们的GitHub wiki](https://github.com/palantir/blueprint/wiki)上，包括我们的[编码指南](https://github.com/palantir/blueprint/wiki/Coding-guidelines)和我们的[开发实践](https://github.com/palantir/blueprint/wiki/Development-Practices)。
