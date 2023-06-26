# web 前端工程师 - 吴同同

## 个人信息

<section style="display: flex; flex-wrap: wrap">
<p style="min-width: 50%;"><span>姓名：</span><span>吴同同</span></p>
<p style="min-width: 50%;"><span>年龄：</span><span>24</span></p>
<p style="min-width: 50%;"><span>学历：</span><span>本科</span></p>
<p style="min-width: 50%;"><span>邮箱：</span><span>wtt150249@gmail.com</span></p>
<p style="min-width: 50%;"><span>GitHub：</span><span>https://github.com/xiaotong-tong</span></p>
</section>

## 技术栈

-   熟练使用 HTML、CSS 和 JavaScript 构建高性能 Web 应用程序，了解 Web Components 规范，具有基础框架开发经验。
-   熟练使用 JavaScript ES6+，了解 JavaScript 模块化开发，具有使用 Rollup 打包工具打包项目的经验。
-   熟悉 Node.js 开发，了解基础 SQL 语句，具有使用 Express 和 Sequelize 开发 API 接口的经验。
-   了解 Vue.js 及其常用组件库，有单页面应用开发经验。
-   具备自动化测试开发技能，具有 Puppeteer 和 Selenium 自动化测试开发经验。
-   熟悉 a11y 适配，具有使用无障碍开发工具检查和修复无障碍问题的经验，能够开发更易于访问和使用的 Web 应用程序。
-   具备日文阅读能力，拥有 N2 等级证书，能够阅读日文文档。

## 教育经历

-   2017 年 9 月 - 2021 年 6 月，宿州学院，软件工程，本科

## 项目经历

### 安徽科大国创软件科技有限公司

#### XUX

工作时间：2020 年 12 月 - 2023 年 6 月 (实习: 2020 年 12 月 - 2021 年 6 月)

项目描述：XUX 是一款基于 jQuery 和 jQuery UI 搭建的 Web 组件库，用于快速搭建浏览器页面以及打印机页面。

项目职责：

-   负责组件库的升级和维护，保证组件库的稳定性和可用性。

    -   跟踪项目依赖库的更新，及时更新项目依赖库，保证项目的健壮性。例如将 jQuery 从 1.10.2 版本升级到 3.6.0 版本，将 jQuery UI 从 1.10.4 版本升级到 1.12.1 版本等。
    -   基于 Puppeteer 的 Coverage 模块，实现在自动化测试运行时检查组件库的测试覆盖率。根据覆盖率结果，新增或修改未覆盖的测试用例，删除失效的组件代码，在减少代码量的同时提高组件库的稳定性和可用性。
    -   使用 axe-core 检查组件库的无障碍性，根据检查结果修改组件库的代码，提高组件库的无障碍性。
    -   在启动 NVDA 屏幕阅读器后，检查组件库的可访问性，确保组件的内容可以被正确读取，以及组件的交互可以被正确执行。

-   完成了小组内部的任务管理系统开发，用于管理小组内部的任务分配和进度管理。
    -   使用 Vue.js 和 Element UI 开发前端页面。(Vue.js 2.x)
    -   使用 Node.js 和 Express 开发后端 API 接口。
    -   使用 Sequelize 操作 MySQL 数据库。

#### MUXJS

工作时间：2022 年 4 月 - 2023 年 6 月

项目描述：MUXJS 是一款基于 Web Components 搭建的 Web 组件库，用于快速搭建浏览器页面以及打印机页面。为 XUX 的重构升级版本。

项目职责：

-   基于 Web Components 和 Scss 开发基础组件库， 包括 Button、Dropdown、Input、Tooltip 等组件。
-   调研并使用 Intl API 实现组件库的国际化功能。代替 XUX 中的 globalize + CLDR 组件库的方式实现国际化功能，大幅度降低了组件库打包后的体积。

### 个人项目

#### xtt-utils

项目地址: https://github.com/xiaotong-tong/xtt-utils

项目描述：xtt-utils 是一款基于 JavaScript 开发的工具库，用于提供一些常用的工具函数。

项目职责：

-   负责 random、string、array、function 等模块的开发。
-   使用 Jest + Puppeteer 实现浏览器环境下的单元测试。
-   使用 GitHub Actions 实现测试和发布以及 GitHub Pages 部署自动化，提高了开发及部署的效率。

#### xtt-msg

项目地址: https://github.com/xiaotong-tong/xtt-msg

项目描述: xtt-msg 是一款基于 JavaScript 开发的字符串解析工具库，可以按照指定的格式解析字符串。

项目职责：

-   使用正则表达式解析字符串中的占位符，根据占位符的类型，使用对应的解析函数解析占位符。占位符支持并列和嵌套。

    例如 `roll(![random]( ![random](1-->>5) -->> ![random](5-->>10) ))` 格式的字符串，会先在 1-5 中随机生成一个数，再在 5-10 中随机生成一个数，最后再在两个数中随机生成一个数，然后对占位符进行替换。例句中的解析结果可能为 `roll(7)`

-   使用 Rollup 打包工具打包项目，使用 Jest 进行单元测试。
-   编写 Playground 页面，用于演示 xtt-msg 的使用方法。
