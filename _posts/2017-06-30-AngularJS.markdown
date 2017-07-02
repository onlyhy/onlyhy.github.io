---
layout: post
title:  "AngularJS学习笔记"
date:   2017-06-30 17:00:00 +00:00
categories: AngularJS
author: onlyhy
---
### 起步
1. 设置开发环境  
   安装node.js和npm，然后全局安装Angular CLI，执行`npm install -g @angular/cli`

2. 创建新项目  
   `ng new my-app`

3. 启动开发服务器  
   `cd my-app`  
   `ng serve --open`

4. 编辑组件  
   CLI为我们创建了第一个Angular组件,它就是名叫app-root的根组件.在./src/app/app.component.ts目录下找到它。打开这个组件文件，可修改title属性，浏览器会自动刷新。  
   打开 src/app/app.component.css 可以给这个组件设置一些样式.

### 开发环境   
   克隆或者下载《快速起步》种子  

### 架构  
   Angular 是一个用 HTML 和 JavaScript 或者一个可以编译成 JavaScript 的语言（例如 Dart 或者 TypeScript ），来构建客户端应用的框架。  
   用 Angular 扩展语法编写 HTML 模板， 用组件类管理这些模板，用服务添加应用逻辑， 用模块打包发布组件与服务。  
   然后，我们通过引导根模块来启动该应用。 Angular 在浏览器中接管、展现应用的内容，并根据我们提供的操作指令响应用户的交互。  
   ![全景图]（C:Users\YellowHappy\onlyhy.github.io\assets\angularjs.png）






