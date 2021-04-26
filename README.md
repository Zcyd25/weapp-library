## 在线借书平台

<img src="https://imageslr.github.io/weapp-library/assets/img/weapp_code.f16279a1.png" width=250 />

**如果你觉得这个仓库有用，请点一个 Star 支持一下我，谢谢！**  
**如果对哪部分代码有疑问或者需要我讲一下设计和开发的整体理念/部分细节，可以开一个 Issue。欢迎大家与我交流。**

> **欢迎关注本项目使用 Taro 重构后的版本**：[taro-library](https://github.com/imageslr/taro-library)，仅包含三个示例页面，非常简单。面向人群主要是 Taro/React/Redux 的初学者，目的是提供一个简单的实践项目，帮助理解 Taro 与 Redux 的配合方式与 Taro 的基本使用。本项目还提供了一个快速搭建本地 mock 服务的解决方案。

### 运行 Mock Server
本项目目前仅提供小程序的开源代码，暂无对应后端服务。需要自行在本地启动 Mock Server。

在项目目录下安装依赖：
```
npm install
```

启动 Mock Server：
```
gulp mock
```

默认启动端口是 3000，如有区别，请修改 `api/request.js` 中的 `BASE_URL` 常量。

如果在 mac 启动时报错：“无法打开 fse.node：来自身份不明的开发者“，请前往“系统设置 - 安全性与隐私 - 通用 - 允许从以下位置下载的 App”，点击“仍然允许“，然后再次执行 `gulp mock`。这里可能会有两次错误。

这个功能拆分到了单独的仓库里，请查看 [simplest-mock-server](https://github.com/imageslr/simplest-mock-server)，一个开箱即用的搭建本地 mock 接口的工具。

### 云托管

本项目的线上版本使用微信开放平台的云开发能力部署 mock server，从而提供在线预览功能。以下是操作步骤，主要参考了[云托管文档 - 使用指南](https://developers.weixin.qq.com/miniprogram/dev/wxcloud/guide/container/guidance.html)：
1. 开通云托管，创建一个服务
2. 将 mock server 所需文件打包为一个单独的文件夹，运行命令写在 Dockerfile 中，见 [weapp-library-cloud](https://github.com/imageslr/weapp-library-cloud)
3. 在云托管中创建服务版本，本地上传文件夹，监听端口设置为 `3000`
4. 修改小程序中调用接口的代码，将 `wx.request` 改为 `wx.cloud.callContainer`，参考 [cloud](https://github.com/imageslr/weapp-library/tree/cloud) 分支的 [最新提交](https://github.com/imageslr/weapp-library/commit/874617d640bcc98e75682d5aa1298bd4fc78844d)

### 文档
[点击查看](https://imageslr.github.io/weapp-library)

### UI
![ui](./ui.png)

### 组件化
在线借书平台小程序——我的——组件展示

![组件展示](./component.png)

### 文件结构

```
.
├── apis                  // 网络请求封装
├── app.js
├── app.json
├── app.wxss
├── component-demos       // 组件展示
├── components            // 可复用组件
│   ├── async-button      // 异步按钮
│   ├── async-switch      // 异步切换器
│   ├── collapse          // 可折叠容器
│   ├── load-more         // 加载更多
│   ├── no-data           // 暂无数据
│   ├── panel             // 带导航标题的面板
│   ├── popup             // 底部弹出层
│   ├── rate              // 可评半星的评分组件
│   ├── search-bar        // 带遮罩的搜索框
│   ├── send-code         // 发送验证码按钮
│   ├── spinner           // 加载中动画
│   ├── sticky            // 固定页头
│   ├── sticky-2          // 固定页头的另一种实现
│   ├── tab-bar           // 标签页
│   ├── toast             // 弹出提示
│   └── toptip            // 顶部提示
├── images                // 图标
├── package.json
├── pages                 // 页面，子页面在父页面的children文件夹中
│   └─components          // 与业务相关的特殊组件
├── mock                  // Mock Server
│   └── data              // Get/Post/Delete 等接口的 mockjs 模板文件
├── project.config.json
├── styles                // 样式
├── templates             // 模板
│   ├── library-list      // 图书馆列表
│   ├── page-status-indicator // 页面加载状态，带有一个“重新加载”按钮
│   └── showcase          // 图书项目
└── utils                 // 辅助模块
    ├── biz-helper.wxs    // 业务相关辅助函数，用于wxml中
    ├── constant.js       // 业务常量
    ├── constant.wxs      // 业务常量，用于wxml中
    ├── es6-promise.js    // Promise语法支持
    ├── event.js          // 全局事件
    ├── permission.js     // 登录鉴权
    ├── promise-polyfill.js // Promise.finally()语法
    ├── promisify.js      // 微信小程序API Promise化
    ├── qrcode.js         // 二维码生成
    ├── tip.js            // 使用帮助
    ├── utils.js          // 辅助函数
    ├── validator.js      // 正则校验器
    └── fundebug.js       // 错误监控
```

### 代码规范
遵循 [JavaScript Standard Style](https://standardjs.com/readme-zhcn.html)

### 声明
Demo 仅作学习使用, 转载请注明出处。

本作品获得第六届中国软件杯大赛全国一等奖、第一届微信小程序开发大赛华北赛区一等奖。
