+++
draft = true
title = "BootStrap回顾随笔"
date = 2017-07-12T00:00:00+00:00
categories = ["BootStrap"]
authors = ["onlyhy"]
+++

### CDN  
<-- 新 Bootstrap 核心 CSS 文件 -->
`<link href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">`
 
<-- 可选的Bootstrap主题文件（一般不使用） -->
`<script src="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap-theme.min.css"></script>`
 
<-- jQuery文件。务必在bootstrap.min.js 之前引入 -->
`<script src="https://cdn.bootcss.com/jquery/2.1.1/jquery.min.js"></script>`
 
<-- 最新的 Bootstrap 核心 JavaScript 文件 -->
`<script src="https://cdn.bootcss.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>`  



### container 与  container-fluid  

/*0-768px以上宽度container为100%*/
.container {
  padding-right: 15px;
  padding-left: 15px;
  margin-right: auto;
  margin-left: auto;
}
/*768-992px以上宽度container为750px*/
@media (min-width: 768px) {
  .container {
    width: 750px;
  }
}
/*992-1200px以上宽度container为970px*/
@media (min-width: 992px) {
  .container {
    width: 970px;
  }
}
/*1200px以上宽度container为1170px*/
@media (min-width: 1200px) {
  .container {
    width: 1170px;
  }
}

/*container-fluid为100%*/
.container-fluid {
  padding-right: 15px;
  padding-left: 15px;
  margin-right: auto;
  margin-left: auto;
}


### 提示工具与弹出框  
提示工具（Tooltip）插件、弹出框（Popover）插件不像下拉菜单及其他插件那样，它不是纯 CSS 插件。如需使用该插件，必须使用 jquery 激活它（读取 javascript）。使用下面的脚本来启用页面中的所有的提示工具（tooltip）和弹出框(Popover)：
`$(function () { $("[data-toggle='tooltip']").tooltip(); }); ` 

`$(function () { $("[data-toggle='popover']").popover(); });`  

### 代码块  
代码两种显示：code(内联) 或 pre(独立块元素或多行)  开始和结束标签用 ` &lt; 和 &gt; `  

    <p><code>&lt;header&gt;</code> 作为内联元素被包围。</p>
    <p>如果需要把代码显示为一个独立的块元素，请使用 &lt;pre&gt; 标签：</p>
    <pre>
        &lt;article&gt;
            &lt;h1&gt;Article Heading&lt;/h1&gt;
        &lt;/article&gt;
    </pre>  


### 缩写  
`<abbr title="World Wide Web">WWW</abbr><br>` 鼠标悬停会显示完整文本

### 表单  
form>form-group>form-control (input、textarea、select)  
内联表单：.form-inline， .sr-only，可以隐藏内联表单的标签
水平表单： .form-horizontal， .form-group 的 `<div>` ，标签添加 class .control-label
