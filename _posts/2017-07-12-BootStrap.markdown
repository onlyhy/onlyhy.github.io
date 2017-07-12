---
layout: post
title: "BootStrap回顾随笔"
date: 2017-07-12 22:00:00 +00:00
categories: 基础知识
author: onlyhy
---
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
