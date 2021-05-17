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

# 电梯调度器

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

在 [`ElevatorPanel.vue`](/src/components/ElevatorPanel.vue) 中实现了一个电梯内部按钮模块的 UI 以及一台电梯内部运作的逻辑代码。
单个模块的 UI 如下：
