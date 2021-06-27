# Elevator Dispatching Simulator

An elevator dispatching simulator powered by Vew.js and tailwindcss.

Actions below help you deploy the project locally.

You can also check out this project's **[GitHub Page](https://plusonez.github.io/OS-Homework-Elevator-Dispatching/)** to view the online deployment.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```



# 电梯调度器文档

## 环境与运行

本项目依赖于 `npm` 与 `Vue CLI`，运行前请保证环境中已安装 [`Node.js`](https:///nodejs.org/en/)。

在项目根目录下，运行
```
npm install
```
可以下载项目所依赖的文件包。

之后再运行
```
npm run serve
```
可以在本地部署电梯调度模拟器的网页。完成后依照命令行界面的提示便可在浏览器中测试该模拟器，默认运行在计算机 [8080 端口](http://localhost:8080)。

## 访问部署在 GitHub Page 上的电梯调度模拟器

本项目部署在项目[GitHub 仓库](https://github.com/PlusOneZ/OS-Homework-Elevator-Dispatching) 对应的 [GitHub Page](https://plusonez.github.io/OS-Homework-Elevator-Dispatching/) 上，点击前述超链接或是复制 
`https://plusonez.github.io/OS-Homework-Elevator-Dispatching/` 到浏览器便可体验。

## 文件结构
```
├── README.md
├── babel.config.js                                 // babel 配置选项
├── package-lock.json                               // npm 生成的文件
├── package.json                                    // npm 依赖项
├── postcss.config.js                               // 指定 tailwindcss 依赖
├── public
│   ├── favicon.ico
│   └── index.html                                  // 首页
├── src                                             // 源代码文件夹
│   ├── App.vue                                     // 默认生成的文件
│   ├── assets                                      // 资源文件
│   │   ├── css
│   │   │   └── tailwind.css
│   │   └── logo.png
│   ├── components                                  // 逻辑组件
│   │   ├── Elevator.vue                            // 组合与调度代码
│   │   ├── ElevatorPanel.vue                       // 电梯内按钮模块
│   │   └── FloorPanel.vue                          // 楼层内按钮模块
│   └── main.js                                     // index.html 的 js 代码
├── tailwind.config.js                              // tailwind 配置文件
└── vue.config.js                                   // Vew.js 配置文件
```

所有逻辑代码均在 [`src/components`](/src/components) 内，其余部分为架构 Vue.js 项目所需要包含的文件。

## 逻辑架构

### 电梯内按钮盘逻辑

在 [`ElevatorPanel.vue`](/src/components/ElevatorPanel.vue) 中实现了一个电梯内部按钮模块的 UI 以及一台电梯内部运作的逻辑代码。

电梯内部按钮单个模块的 UI 如下：

<img src="https://i.loli.net/2021/05/18/BFRfyJrTvDq4ePX.png" alt="in elevator panel" width="25%">

其中，每个数字按钮都可以点按，左下角显示电梯开关状态，右下角两个按钮分别是"报警"与"呼叫"，"报警"按钮会使该电梯停下。

### 楼层内按钮盘逻辑

在 [`FloorPanel.vue`](/src/components/FloorPanel.vue) 中实现了一个楼层的按钮模块 UI 以及呼叫某台电梯的功能。

楼层内按钮单个模块的 UI 如下：

<img src="https://i.loli.net/2021/05/18/bNQ4pzoyAt1qlM6.png" width="25%" alt="floor panel">

上下按钮可以点按，会有明显的点亮（黄色）、熄灭（灰色）效果。底层的按钮只有"向上"，而顶层的按钮只有"向下"。

### 布局与调度逻辑

在 [`Elevator.vue`](src/components/Elevator.vue) 中实现了多台电梯与多个楼层的排布。通过调整参数可以改变楼层数量与电梯数量，楼层改变后电梯内的按钮数量也会随之改变。

电梯总体布局如下图所示：

![elevator.png](https://i.loli.net/2021/05/18/FV2DhRBuwbN7H1L.png)

## 使用指南

* 通过电梯中的按钮（In Elevator Panel）表示在电梯内设置目标楼层。点击**呼叫**（底部右一）按钮表示呼叫总台功能，点击**报警**（底部右二）按钮来急停电梯并呼叫总台。
* 通过楼层按钮（Floor Panel）来在楼层中呼叫电梯，接下来会有一台电梯在楼内打开门。
* 报警功能使用后，该电梯会失效，再次点击报警按钮可以复原。

## 难点分析

* 通过 `npm run build` 指令生成的可部署文件夹不一定可以在 GitHub Page 上部署成功，需要调整文件结构和引用文件的路径使包生成器能够找到对应文件并打包。
* 按逻辑将电梯分成两部分（电梯内和楼内）之后，实现组件之间的通信需要清晰的设计。本项目中使用了 `this.$emit` 方法来传递事件。
* 电梯调度的算法实现中，我使用了纯逻辑判断的方式实现。先排查是否有同向包含路径的电梯，再从空闲电梯中寻找最近的调度，再找到不同向电梯中回头距离最短的电梯。
* 电梯遇报警暂停后，遗留的指派给该电梯的任务应该要重新被指派给别的电梯，全部电梯停止后应该使所有楼层的按钮都失效。
* UI 的排布使用了手写 html 的方式，若直接写会难以调整，本项目采用了 `tailwindcss` 自带的[网页 Playground](https://play.tailwindcss.com/) 时时渲染。
* 由于是 `Vue.js` 生成的 JavaScript 代码，报错的位置难以排查，只能通过添加浏览器 `log` 的信息来判断。

## 坑点排查

* `Vue.js` 更新监听中的数组时应该使用 `this.$set` 方法，而不能直接赋值。
* 在 `tailwind.config.js` 中调整 `purge` 参数使项目排除未使用的 `css` 类别，生成的打包文件会明显减小。
* `tailwind` 因为 `postcss`版本问题只能安装适配版，因此需要调整一些类别的使用。

## 不足之处
* 调度的算法并不是最优解，有些不同于实际调度的反常费事情况。
* 代码实现中有冗余，可以进一步优化。
* 每次将楼层内的呼叫指派到某台电梯后并不会根据电梯的情况动态的修改，一定要等到指派的电梯停在该楼层。