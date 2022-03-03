# Flutter

* 主页
* 简介
* 安装
* 使用 Android Studio 创建简单应用
* Flutter 应用的体系结构
* Dart 编程简介
* Widgets 简介
* Layouts 简介
* Gestures 简介
* State Management
* Animation
* 编写 Android 代码
* 编写 iOS 代码
* Package
* REST API
* DataBase
* 国际化
* Testing
* Deployment
* Development Tools
* 编写高级应用
* 总结

## 主页

Flutter 是谷歌开源的一个框架。它可以帮助我们去创建高质量、高性能跨平台(Android、iOS)的应用。

它提供一个简单、强大、高效和易理解的 SDK 去编写移动端应用。

前置知识就是需要去了解 dart 、android 基本知识点，同样需要掌握面向对象编程。

## 简介

一般来说，开发一款移动应用是复杂和具有挑战的任务。有很多框架可用于去开发移动应用。 Android 提供 native 框架它是基于 Java 语言。 iOS 提供 native 框架它是基于 ``Objective-C`` / ``Swift`` 语言。

然后，想要去开发一个应用同时支持两个平台，你需要使两个不同的框架去编写。 为了帮助避免这种复杂性，存在支持两个平台的框架。这些框架包括基于简单 HTML 的 hybrid 移动应用(使用 HTML 编写用户界面，JavaScript 编写应用逻辑)到复杂语言的特定框架(通过把开发语言通过工具转换为原生代码)。 不管它的简单性和复杂性如何，这些框架都有很多缺点，其中比较大的缺点就是性能慢。

在这种情况下，Flutter -- 一个基于 Dart 语言的简单和高性能的框架，之所以高性能，它是直接在操作系统上绘制界面，并不是通过 native 框架。


Flutter 提供许多现成的 ``widgets``(UI) 去创建现代应用。这些 widgets 针对移动环境进行相应的优化且在使用时同 HTML 一样简单。

具体来讲，Flutter 应用它自身就是一个 widget(皆 widget)。Flutter widgets 也支持动画 和 手势。应用逻辑基于响应式编程。 Widget 可以选择拥有 state。通过更改 widget 对应的 state，Flutter 将自动比较新老的状态并且找到需要更改的内容并重新渲染它。

### Flutter 的特点

Flutter 框架为开发人员提供以下功能:

* 响应式框架
* 使用 Dart 编程语言，它非常容易学习
* 开发快
* 漂亮和流畅的用户界面
* 同套代码可运行在多个平台
* 高性能应用

### Flutter 的优点
* Dart 有一个庞大的软件包库，可以让扩展你的应用程序
* 开发人员只需要编写一套代码，就可以运行多个平台
* 编写更少的测试用例
* Flutter 简单使用使它成为快速开发的理想选择， 它的定制能力和可扩展性使它更加强大
* 使用 Flutter ，开发者可以完全控制小部件和布局
* Flutter 提供了出色的开发工具，具强大热更新能力。极大提高开发体验及效率。

### Flutter 的缺点
* 基于 Dart 语言，那么开发者需要要学习新语言。
* 现在框架是图分离视图和逻辑，但在 Flutter 中，视图与逻辑是耦合在一起的。不过可以通过一些方式去克服这个问题。

## 安装

推荐步骤:
* 先安装 Flutter
* 通过 Flutter doctor 命令，检测环境是否安装完成。
* 依次安装

### Windows
> https://docs.flutter.dev/get-started/install/windows
### MAC
> https://docs.flutter.dev/get-started/install/macos

## Flutter 应用的体系结构

### Widgets

widget 是 Flutter 中的核心概念，一切都是 widget。 widget 构建应用的基础。

在 Flutter 中，应用自身就是一个 widget。该应用是顶级的 widget ，其应用 UI 界面通过一个或多个子 widget 构建，
这些子 widget 再次使用其子 widget 构建。 这种组合功能帮助我们创建任何复杂的用户界面。


### Gestures

Flutter 通过特殊的 GestureDetector widget 来支持交互。GestureDetector 是一个不可见的 widget，它能够捕获用户交互。例如对其子 widget 的点击，拖拽等。Flutter 内部提供原生组件大部分都是通过 GestureDetector 来支持交互。

### State 概念

在 Flutter 中的 widget 根据状态分为两种，一种有状态 ``StatefulWidget``、另一种无状态 ``StatelessWidget``。如果一个 widget 需要支持状态维护，则需要去继承 ``StatefulWidget``。拥有状态的 widget 是响应式的。这与 reactjs 类似，StatefulWidget 会根据内部状态发生更改时自动触发重新渲染。 通过找出新旧差异并仅渲染必要的更改来优化重新渲染。

### Layers

Flutter 设计是一个可扩展的分层系统。它作为一系列独立的库存在，每个库都依赖于底层。任何层都没有特权访问下面的层，并且框架层的每个部分都被设计为可选和可替换的。

<img src="./images/archdiagram.png"/>

对于底层的操作系统，Flutter 应用程序的封装方式与任何其它的原生应用程序相同。``platform-specific embedder`` 提供了一个入口点； 与底层操作系统协调以访问表层渲染设置、可访问性和输入等服务；并管理消息的事件循环。``embedder`` 使用适合平台的语言编写的。目前 Java 和 C++  用于 Android， Objective-C/Objective-C++ 用于 iOS 和 macOS，C++ 用于 Windows 和 Linux。使用 ``embedder`` , Flutter 代码可以作为一个模块集成到现有的应用程序中，或者代码可能是应用程序的全部内容。Flutter 包含许多用于常见目标 platform 的 ``embedder``。

Flutter 的核心是 **Flutter engine**。它大部分是用 C++ 编写的，并支持所有 Flutter 应用程序所需的原生语言。每当需要绘制新帧时，引擎负责对合成场景进行渲染。它提供了 Flutter 核心 API 的底层实现，包括图形（通过Skia）、文本布局、文件和网络 I/O、可访问性支持、插件架构以及 Dart 运行时和编译工具链。

通过 ``dart:ui`` 把底层封装好的 C++ 代码暴露给 Flutter 框架，该库开发了底层的原语，例如 用于驱动输入、图形和文本渲染子系统的类。

通常，开发人员通过 Flutter 框架进行交互，该框架提供了一个用 Dart 语言编写的现代的响应式框架。它包含一组丰富的 platform，布局和基础库，由一系列层组成。从下到上，我们有:

* 基础类和构建服务，如 动画、绘画 和 手势，它们在底层基础上提供常用的抽象。
* 渲染层提供了处理布局的抽象。使用此层，您可以构建可渲染对象树。您可以动态操作这些对象，树会自动更新布局以反映您的更改。
* widgets 层是一个组合抽象，渲染层中的每个渲染对象在 widget 层中都有一个对应的类。此外，widget 层允许您定义可以重用的类组合。这是引入响应式编程模型的层。
* Material 和 Cupertino 库提供了全面的控件集，这些控件使用 widget 层的组合原语来实现 ``Material`` 或 ``iOS`` 设计语言。

Flutter 框架比较小；开发可以使用许多高级的功能它们分别通过包的方式提供，包括像 camera 和 webview 这样的平台插件，以及在核心 Dart 和 Flutter 库上构建的 ``characters``、``http`` 和 ``animations`` 等与平台无关的功能。其它一些软件包来自更广泛的生态系统，覆盖 ``APP内支付``，``Apple 身份认证`` 和 ``animations`` 等服务。

