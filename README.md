<img height="204" src="https://cloud.githubusercontent.com/assets/464822/20228152/d3f36dc2-a804-11e6-80ff-51ada2d13ea7.png">

# [Blueprint](http://blueprintjs.com/) [![CircleCI](https://circleci.com/gh/palantir/blueprint.svg?style=svg&circle-token=4725ab38f16004566d6430180663d7e7f9f5da9d)](https://circleci.com/gh/palantir/blueprint)

Blueprint是一个针对web的，基于React的UI toolkit。

针对_desktop applications_，它为构建复杂的，数据密集的Web界面进行了优化。
如果您严重依赖移动交互，并且正在寻找一个移动优先的UI工具包，Blueprint可能不适合您。

[**查看完整的文档 ▸**](http://blueprintjs.com/docs)

[**阅读我们在wiki上的FAQ ▸**](https://github.com/palantir/blueprint/wiki/Frequently-Asked-Questions)

[**阅读介绍博客 ▸**](https://medium.com/@palantir/scaling-product-design-with-blueprint-25492827bb4a)

**支持问题**？ 我们使用 [Stack Overflow 上的 blueprintjs 标签 ▸](http://stackoverflow.com/questions/tagged/blueprintjs)

## 包

这个存储库包含`packages/`目录下的多个项目，分为三类：

### 库

这些是我们发布到NPM的组件库。

- [![npm](https://img.shields.io/npm/v/@blueprintjs/core.svg?label=@blueprintjs/core)](https://www.npmjs.com/package/@blueprintjs/core) &ndash; 核心样式和组件。
- [![npm](https://img.shields.io/npm/v/@blueprintjs/datetime.svg?label=@blueprintjs/datetime)](https://www.npmjs.com/package/@blueprintjs/datetime) &ndash; 用于与日期和时间交互的组件。
- [![npm](https://img.shields.io/npm/v/@blueprintjs/docs.svg?label=@blueprintjs/docs)](https://www.npmjs.com/package/@blueprintjs/docs) &ndash; [Documentalist](https://github.com/palantir/documentalist) 数据的文档主题。
- [![npm](https://img.shields.io/npm/v/@blueprintjs/table.svg?label=@blueprintjs/table)](https://www.npmjs.com/package/@blueprintjs/table) &ndash; 可扩展交互式表格组件。
- [![npm](https://img.shields.io/npm/v/@blueprintjs/labs.svg?label=@blueprintjs/labs)](https://www.npmjs.com/package/@blueprintjs/labs) &ndash; Incubator and staging area for new components still under initial development.

### 应用程序

这些在GitHub Pages上作为静态Web应用程序托管：

- `docs-app` &ndash; 文档站点在blueprintjs.com/docs
- `landing-app` &ndash; 在blueprintjs.com的Landnig页面

这些被用作开发playground的环境：

- `table-dev-app` &ndash; 演示页面，支持所有表格功能的手动测试

### 构建工具

这些私有包定义了开发依赖并包含构建配置。它们遵循标准的NPM包layout，它允许我们为构建配置和隔离`devDependencies`组保持清晰的API边界。未来，我们可能会发布这些软件包，以允许其他Blueprint项目在这个monorepo之外使用这个基础设施。

- `karma-build-scripts`
- `node-build-scripts`
- `tslint-config`
- `webpack-build-scripts`

## 开发

[Lerna](https://lernajs.io/)管理这个monorepo中的包间依赖关系。
版本是通过`lerna run`和NPM脚本编排的。

__前提__: Node.js v8+, Yarn v1.0+

### 一键安装

克隆这个repo之后，运行：

1. `yarn` 安装所有的依赖。
1. `yarn verify` 确保您的所有构建工具正常工作。

### 合并上游变更

如果您以前处于工作状态，并且刚刚从`develop`中提取了新的代码：

- 如果存在程序包依赖性更改，请在根目录下运行`yarn`。
  - 如果没有新东西要安装，这个命令会非常快完成。
- 运行`yarn compile-libs`来获取这个仓库中库包的最新版本。
  - 这个命令比`yarn verify`快，因为它不会构建应用程序包（`docs-app`，`landing-app`等）或运行测试

### 开发库

每个库都有自己的开发脚本，您可以运行它来监控对该软件包的更改，并使用webpack-dev-server运行文档应用程序：`yarn dev:core`，`yarn dev:datetime`等。

- `table`&mdash;是一个例外，因为它有自己的开发应用程序，`dev:table`脚本，不用运行docs站点。
  - 使用packages/table-dev-app文件夹中的`yarn dev`运行table开发应用程序。
- 您也可以选择通过从根目录运行`yarn dev:all`来监视所有软件包的更改。

### 更新依赖关系

1. 编辑你想改变依赖关系的`package.json`。
1. 在根目录下运行`yarn`来更新锁文件。
1. 提交结果。

### 更新文档

许多Blueprint的文档都存在于源代码中，因为JSDoc在`.tsx？`文件中注释，在`.scss`文件中有KSS标记。这个文档被[documentalist](https://github.com/palantir/documentalist/)提取和转换为JSON数据来生成的。

如果您正在更新文档来源（而不是位于`packages/docs-app`中的文档UI代码），则需要从`docs-app`包运行`yarn generate-docs-data`以查看它在应用程序中的反映。请注意，这个包中的`yarn bundle`也运行这个脚本。

### 更新图标

在这个仓库中，[一键安装](#one-time-setup)和[合并上游变更](#incorporating-upstream-changes)步骤应产生生成的源代码，用于建立图标文档。这对大多数开发工作流程来说已经足够了。
如果您正在更新图标或添加新图标，则需要在`packages/core`中运行`yarn compile`，以查看运行任何dev脚本之前所反映的更改。

## 贡献

寻找有助于代码库的地方？看看
[Status: accepting PRs](https://github.com/palantir/blueprint/labels/Status%3A%20accepting%20PRs)标签。

阅读我们的[贡献指南](https://github.com/palantir/blueprint/blob/master/CONTRIBUTING.md)和[开发实践](https://github.com/palantir/blueprint/wiki/Development-Practices)，为您的PR提供最好的合并机会。

## 许可证

该项目在[Apache-2.0许可证](https://github.com/palantir/blueprint/blob/master/LICENSE)下提供使用。
