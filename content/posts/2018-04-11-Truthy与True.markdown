+++
draft = true
title = "Truthy与True的不同"
date = 2018-04-11T00:00:00+00:00
categories = ["JavaScript"]
authors = ["onlyhy"]
+++

黄黄说：“点点滴滴都是真”

读Vue.js的官方文档，注意到了Truthy，记一下[MDN](https://developer.mozilla.org/zh-CN/docs/Glossary/Truthy)的解释。

### Truthy（真值）

在JS中，Truthy指在Boolean（布尔型）上下文中转换后的值为真的值，*布尔型是一种逻辑数据类型，只能有true或false值*。

除非被定义为falsy（false,0,"",undefined,NaN）,否则所有值都为真值。

JS中真值示例：

    if (true)
    if ({})
    if ([])
    if (42)
    if ("foo")
    if (new Date())
    if (-42)
    if (3.14)
    if (-3.14)
    if (Infinity)
    if (-Infinity)



To Be Continued…
