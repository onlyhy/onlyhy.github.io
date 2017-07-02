---
layout: post
title:  "AngularJS学习笔记（一）"
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

   ![全景图](C:\Users\YellowHappy\onlyhy.github.io\assets\angularjs.png)

   共8个主要构造块：模块 (module)，组件 (component)，模板 (template)，元数据 (metadata)，数据绑定 (data binding)，指令 (directive)，服务 (service)，依赖注入 (dependency injection)  

#### 模块  
   Angular 应用是模块化的，并且 Angular 有自己的模块系统，它被称为 Angular 模块或 NgModules。
   每个Angular应用至少有一个模块（根模块），习惯命名为AppModule。  
   Angular 模块（无论是根模块还是特性模块）都是一个带有@NgModule装饰器的类。装饰器是修饰JS类的函数。  
   NgModule是一个装饰器函数，接收一个用来描述模块属性的元数据对象。  

   declarations - 声明本模块中拥有的视图类。Angular 有三种视图类：组件、指令和管道。  
   exports - declarations 的子集，可用于其它模块的组件模板。  
   imports - 本模块声明的组件模板需要的类所在的其它模块。  
   providers - 服务的创建者，并加入到全局服务列表中，可用于应用任何部分。  
   bootstrap - 指定应用的主视图（称为根组件），它是所有其它视图的宿主。只有根模块才能设置bootstrap属性  

   根模块例子：

    import { NgModule }      from '@angular/core';
    import { BrowserModule } from '@angular/platform-browser';
    @NgModule({
     imports:      [ BrowserModule ],
     providers:    [ Logger ],
     declarations: [ AppComponent ],
     exports:      [ AppComponent ],
     bootstrap:    [ AppComponent ]
    })

##### 模块库  
   Angular 提供了一组 JavaScript 模块。可以把它们看做库模块。每个 Angular 库的名字都带有@angular前缀。用 npm 包管理工具安装它们，用 JavaScript 的import语句导入其中某些部件。
   
    import { BrowserModule } from '@angular/platform-browser';

   要访问这些素材，需要加入加入@NgModule元数据的imports中：  
    
    imports:      [ BrowserModule ],

#### 组件  
   控制屏幕上的一小块区域，称为视图。

#### 模板  
   模板以 HTML 形式存在，告诉 Angular 如何渲染组件。

#### 元数据  
   告诉Angular如何处理一个类，在TypeScript中，用装饰器 (decorator) 来附加元数据。  

#### 数据绑定  
   让模板的各部分与组件的各部分相互合作，往模板 HTML 中添加绑定标记，来告诉 Angular 如何把二者联系起来。  
   数据绑定的语法有四种形式，每种形式都有一个方向 —— 绑定到 DOM 、绑定自 DOM 以及双向绑定。  

    <li>{{hero.name}}</li>
    <hero-detail [hero]="selectedHero"></hero-detail>
    <li (click)="selectHero(hero)"></li>

   {{hero.name}} 插值表达式，[hero]属性绑定，(click)事件绑定  
   双向数据绑定最重要，用ngModel指令组合了属性绑定和事件绑定的功能  

    <input [(ngModel)]="hero.name">

#### 指令  
   模板根据指令提供的操作对DOM进行操作。组件是一个带模板的指令；@Component装饰器实际上就是一个@Directive装饰器，只是扩展了一些面向模板的特性。  
   两种其它类型的指令：结构型指令和属性 (attribute) 型指令。  
   结构型指令通过在 DOM 中添加、移除和替换元素来修改布局。  

    <li *ngFor="let hero of heroes"></li>
    <hero-detail *ngIf="selectedHero"></hero-detail>

   *ngFor告诉 Angular 为heroes列表中的每个英雄生成一个<li>标签。
   *ngIf表示只有在选择的英雄存在时，才会包含HeroDetail组件。  

   属性型 指令修改一个现有元素的外观或行为。 在模板中，它们看起来就像是标准的 HTML 属性。 

    <input [(ngModel)]="hero.name">

   Angular 还有少量指令，它们或者修改结构布局（例如 ngSwitch）， 或者修改 DOM 元素和组件的各个方面（例如 ngStyle和 ngClass），也能自定义指令。  

#### 服务
   包括：值、函数，或应用所需的特性，几乎任何东西都可以是一个服务，典型的服务是一个类。

#### 依赖注入
   是提供类的新实例的一种方式，负责处理好类所需的全部依赖，提供新组件以及组件所需的服务。  
   当 Angular 创建组件时，会首先为组件所需的服务请求一个注入器 (injector)，注入器存放着以前创建的实例，如果所请求的服务实例不在容器中，注入器就会创建一个服务实例，并且添加到容器中，然后把这个服务返回给 Angular。 当所有请求的服务都被解析完并返回时，Angular 会以这些服务为参数去调用组件的构造函数。，这就是依赖注入 。  
   要点：
   1. 依赖注入渗透在整个 Angular 框架中，被到处使用。
   2. 注入器 (injector) 是本机制的核心。
   注入器负责维护一个容器，用于存放它创建过的服务实例。
   注入器能使用提供商创建一个新的服务实例。
   3. 提供商是一个用于创建服务的配方。
   4. 把提供商注册到注入器。  

#### 其他特性和服务  
   动画：用 Angular 的动画库让组件动起来，而不需要对动画技术或 CSS 有深入的了解。

   变更检测：变更检测文档会告诉你 Angular 是如何决定组件的属性值变化，什么时候该更新到屏幕， 以及它是如何利用区域 (zone) 来拦截异步活动并执行变更检测策略。

   事件：事件文档会告诉你如何使用组件和服务触发支持发布和订阅的事件。

   表单：通过基于 HTML 的验证和脏检查机制支持复杂的数据输入场景。

   HTTP：通过 HTTP 客户端，可以与服务器通讯，以获得数据、保存数据和触发服务端动作。

   生命周期钩子：通过实现生命周期钩子接口，可以切入组件生命中的几个关键点：从创建到销毁。

   管道：在模板中使用管道转换成用于显示的值，以增强用户体验。例如，currency管道表达式：

         price | currency:'USD':true  
         
   它把价格“42.33”显示为$42.33。

   路由器：在应用程序客户端的页面间导航，并且不离开浏览器。

   测试：使用 Angular 测试平台，在你的应用部件与 Angular 框架交互时进行单元测试。








