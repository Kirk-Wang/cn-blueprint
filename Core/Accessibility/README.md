# 无障碍性{#Accessibility}

Blueprint致力于提供开箱即用的无障碍组件。 许多JS组件将应用无障碍的HTML属性来支持不同的使用模式。

## 焦点管理{#Focus-management}

焦点状态（活动元素周围的亮蓝色轮廓）对键盘导航至关重要，以指示哪个元素当前处于活动状态。 在使用鼠标时，它们不那么重要，有时甚至是彻头彻尾的侵入，因为您可以随时点击任意位置。

Blueprint包含一个管理焦点样式外观的实用程序。 启用时，用户使用鼠标进行交互时，焦点样式将被隐藏，并在按tab键以开始键盘导航时出现。在下面尝试一下。

**您必须在您的应用程序中明确启用此功能（并且您可能想要）：**

```ts
import { FocusStyleManager } from "@blueprintjs/core";

FocusStyleManager.onlyShowFocusOnTabs();
```

请注意，文本输入的焦点样式（稍厚的彩色边框）不会被此实用程序删除，因为知道您输入的位置总是有用的。

@reactExample FocusExample

### JavaScript API{#JavaScript-API}

这种行为由位于__@blueprintjs/core__包中的名为`FocusStyleManager`的单例控制。 它支持以下公共方法：

- `FocusStyleManager.isActive(): boolean`：返回`FocusStyleManager`当前是否正在运行。
- `FocusStyleManager.onlyShowFocusOnTabs(): void`：在鼠标交互过程中启用隐藏焦点样式的行为。
- `FocusStyleManager.alwaysShowFocus(): void`：停止这种行为（焦点样式始终可见）。

## 色彩对比{#Color-contrast}

颜色被设计为尽可能多的人可以访问，即使是那些视力受损或遭受任何色盲的人也是如此。 我们的颜色不仅被选择在一起，而且还遵守[WCAG 2.0](https://www.w3.org/TR/WCAG20/) 标准。
