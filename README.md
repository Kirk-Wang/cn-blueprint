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

If you were previously in a working state and have just pulled new code from `develop`:

- If there were package dependency changes, run `yarn` at the root.
  - This command is very quick if there are no new things to install.
- Run `yarn compile-libs` to get the latest built versions of the library packages in this repo.
  - This command is quicker than `yarn verify` since it doesn't build the application packages (`docs-app`, `landing-app`, etc.) or run tests

### Developing libraries

Each library has its own dev script which you can run to watch changes to that package and run the docs application with webpack-dev-server: `yarn dev:core`, `yarn dev:datetime`, etc.

- One exception is `table`&mdash;since it has its own dev application, the `dev:table` script doesn't run the docs site.
  - Run the table dev application using `yarn dev` in the packages/table-dev-app folder.
- You may also choose to watch changes across all packages by running `yarn dev:all` from the root directory.

### Updating dependencies

1. Edit the `package.json` where you wish to change dependencies.
1. Run `yarn` at the root to update lockfiles.
1. Commit the result.

### Updating documentation

Much of Blueprint's documentation lives inside source code as JSDoc comments in `.tsx?` files and KSS markup in `.scss` files. This documentation is extracted and converted into static JSON data using [documentalist](https://github.com/palantir/documentalist/).

If you are updating documentation sources (_not_ the docs UI code which lives in `packages/docs-app`), you'll need to run `yarn generate-docs-data` from the `docs-app` package to see it reflected in the application. Note that `yarn bundle` in this package also runs this script.

### Updating icons

The [One-time setup](#one-time-setup) and [Incorporating upstream changes](#incorporating-upstream-changes) steps should produce the generated
source code in this repo used to build the icons documentation. This is sufficient for most development workflows.

If you are updating icons or adding new ones, you'll need to run `yarn compile` in `packages/core` to see those changes reflected before
running any of the dev scripts.

## Contributing

Looking for places to contribute to the codebase? Check out the
[Status: accepting PRs](https://github.com/palantir/blueprint/labels/Status%3A%20accepting%20PRs) label.

Read about our [contribution guidelines](https://github.com/palantir/blueprint/blob/master/CONTRIBUTING.md) and
[development practices](https://github.com/palantir/blueprint/wiki/Development-Practices) to give your PR
its best chance at getting merged.

## License

This project is made available under the [Apache-2.0 License](https://github.com/palantir/blueprint/blob/master/LICENSE).
