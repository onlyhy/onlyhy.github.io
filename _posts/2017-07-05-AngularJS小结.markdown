---
layout: post
title: "菜鸟教程AngularJS文档小结"
date: 2017-07-05 07:00:00 +00:00
categories: AngularJS
author: onlyhy
---
#### 叽里咕噜
 哇，之前的笔记好写了多字哇 ，简单点，笔记的方式简单点

## 参考手册
   <a>http://www.runoob.com/angularjs/angularjs-reference.html</a>  

### 简介  
#### 扩展HTML
   AngularJS 通过 ng-directives 扩展了 HTML。
   ng-app 指令定义一个 AngularJS 应用程序。
   ng-model 指令把元素值（比如输入域的值）绑定到应用程序。
   ng-bind 指令把应用程序数据绑定到 HTML 视图。  

#### AngularJS是啥
   AngularJS 把应用程序数据绑定到 HTML 元素。
   AngularJS 可以克隆和重复 HTML 元素。
   AngularJS 可以隐藏和显示 HTML 元素。
   AngularJS 可以在 HTML 元素"背后"添加代码。
   AngularJS 支持输入验证

#### 指令
   是指以ng作为前缀的HTML属性。
   H5允许扩展的属性以data-开头，AngularJS属性以ng-开头，ng-data-让网页对H5有效。
#### 表达式  
   使用表达式把数据绑定到HTML,与ng-bind有异曲同工之妙，写在双大括号内，很像JS表达式，可以包含文字、运算符、变量.  

#### 应用  
   View(视图)，即HTML
   Model(模型)，当前视图中可用的数据
   AngularJS 模块（Module） 定义了 AngularJS 应用。
   一个网页可以包含多个运行在不同元素中的AngualrJS应用程序

    var app = angular.module('myApp', []);

   AngularJS 控制器（Controller） 用于控制 AngularJS 应用，可以添加或修改属性。

    app.controller('myCtrl', function($scope) {
    $scope.firstName= "John";
    $scope.lastName= "Doe";
    });

   ng-app指令定义了应用, ng-controller 定义了控制器。  

### 表达式  
   AngularJS数字、字符串、对象、数组都与JS相似。  
   与JS表达式相比：
   1. 可写在HTML中  
   2. 不支持条件判断，循环及异常
   3. 支持过滤器  
   
### 指令  
   带有前缀ng-

#### ng-app 指令  
   初始化一个 AngularJS 应用程序，定义了应用的根元素

#### ng-init 指令
   初始化应用程序数据

#### ng-model 指令  
  用于表单元素，支持双向绑定，对普通元素无效  

    <div ng-app="myApp" ng-controller="myCtrl">
    名字: <input ng-model="name">
    <h1>你输入了: {{name}}</h1>
    </div>  

  把元素值（比如输入域的值）绑定到应用程序  
  为应用程序数据提供类型验证（number、email、required）。
  为应用程序数据提供状态（invalid、dirty、touched、error）。
  为 HTML 元素基于它们的状态提供 CSS 类。
  绑定 HTML 元素到 HTML 表单。
  可配合双大括号表达式进行数据绑定  

    <div ng-app="" ng-init="quantity=1;price=5">
    <h2>价格计算器</h2>
    数量： <input type="number"    ng-model="quantity">
    价格： <input type="number" ng-model="price">
    <p><b>总价：</b> {{ quantity * price }}</p>
    </div>

#### ng-bind 指令
   和双大括号同时使用时，ng-bind绑定的值覆盖该元素内容  
   用于普通元素，不能用于表单元素，应用单向地渲染数据到元素。
#### ng-repeat 指令 
   ng-repeat指令，对于集合或数组中每个项克隆一次HTML元素

    <div ng-app="" ng-init="names=['Jani','Hege','Kai']">
      <p>使用 ng-repeat 来循环数组</p>
      <ul>
    <li ng-repeat="x in names">
      {{ x }}
    </li>
      </ul>
    </div>  

#### 自定义指令  
   用.directive函数添加自定义指令，在HTML元素上添加自定义指令名。
   使用驼峰法命名一个指令，但在使用它时需要以-分割。
   调用指令通过以下几种方式：元素，名，属性，类名，注释。

    <body ng-app="myApp">
    <runoob-directive></runoob-directive>
    <script>
    var app = angular.module("myApp", []);
    app.directive("runoobDirective", function() {
        return {
            template : "<h1>自定义指令!</h1>"
        };
    });
    </script>
    </body>  

   通过添加restrict属性，设置值，可限制指令调用的方式。
   E：元素，A：属性，C：类名，M：注释，默认是EA  
 
### 作用域  
   Scope是应用在HTML(视图)和JS(控制器)之间的纽带，是一个对象，有可用的方法和属性。

#### 使用  
   在创建控制器时，将$scope对象当做一个参数传递，这样HTML就可以获取属性。

#### 作用范围  
   HTML DOM中会有多个作用域，需要知道scope对应的作用域。

#### 根作用域  
   所有应用都有一个$rootScope,可作用在ng-app指令包含的所有HTML元素中。
   用rootscope定义的值，可以在各个controller中使用。

    <div ng-app="myApp" ng-controller="myCtrl">
    <h1>{{lastname}} 家族成员:</h1>
    <ul>
        <li ng-repeat="x in names">{{x}} {{lastname}}</li>
    </ul>
    </div>
    <script>
    var app = angular.module('myApp', []);
    app.controller('myCtrl', function($scope, $rootScope) {
        $scope.names = ["Emil", "Tobias", "Linus"];
        $rootScope.lastname = "Refsnes";
    });
    </script>

### 控制器  
   ng-controller指令定义了应用程序控制器，控制器是JS对象。

    <div ng-app="myApp" ng-controller="personCtrl">
    名: <input type="text" ng-model="firstName"><br>
    姓: <input type="text" ng-model="lastName"><br>
    <br>
    姓名: {{fullName()}}
    </div>
    <script>
    var app = angular.module('myApp', []);
    app.controller('personCtrl', function($scope) {
        $scope.firstName = "John";
        $scope.lastName = "Doe";
        $scope.fullName = function() {
            return $scope.firstName + " " + $scope.lastName;
        }
    });
    </script>

#### 控制器方法  
   控制器也可以有方法（变量和函数），见上例fullName()

#### 外部文件中的控制器  
   大型应用中，将控制器存储在外部文件中，将代码放在一个js外部文件中，用script标签链入。

### 过滤器  
   使用管道字符添加到表达式和指令中。
   <table>
   <tr>
   <td>currency</td>
   <td>格式化数字为货币格式</td>
   </tr>
   <tr>
   <td>filter</td>
   <td>从数组项中选择一个子集</td>
   </tr>
   <tr>
   <td>number</td>
   <td>格式化保留小数</td>
   </tr>
   <tr>
   <td>orderBy</td>
   <td>根据某个表达式排列数组</td>
   </tr>
   <tr>
   <td>uppercase/lowercase</td>
   <td>格式化字符串为大写/小写</td>
   </tr>
   <tr>
   <td>date</td>
   <td>格式化日期</td>
   </tr>
   <tr>
   <td>limitTo</td>
   <td>截取位数</td>
   </tr>
   </table>

#### 表达式中添加过滤器  

    <div ng-app="myApp" ng-controller="personCtrl">
    <p>姓名为 {{ lastName | uppercase }}</p>
    </div>

#### 向指令添加过滤器  

    <div ng-app="myApp" ng-controller="namesCtrl">
    <ul>
      <li ng-repeat="x in names | orderBy:'country'">
        {{ x.name + ', ' + x.country }}
      </li>
    </ul>
    </div>

#### 过滤输入  

    <div ng-app="myApp" ng-controller="namesCtrl">
    <p><input type="text" ng-model="test"></p>
    <ul>
      <li ng-repeat="x in names | filter:test | orderBy:'country'">
        {{ (x.name | uppercase) + ', ' + x.country }}
      </li>
    </ul>
    </div>

#### 自定义过滤器  

    var app = angular.module('myApp', []);
    app.controller('myCtrl', function($scope) {
    $scope.msg = "Runoob";
    });
    app.filter('reverse', function() { //可以注入依赖
    return function(text) {
        return text.split("").reverse().join("");
    }
    });


