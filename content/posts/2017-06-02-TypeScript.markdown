+++
draft = true
title = "TypeScript基础知识"
date = 2017-06-02T00:00:00+00:00
categories = ["TypeScript"]
authors = ["onlyhy"]
+++

### 简介  
  TypeScript是JS的一个超集（以下简称TS），扩展了JS的语法。因此现有的JS代码可与TS一起工作不用修改，TS通过类型注解提供编译时的静态类型检查。TS可处理已有的JS代码，并只对其中的TS代码进行编译。  

### 语法特性  
  类 Classes  
  接口 Interfaces  
  模块 Modules   
  类型注解 Type annotations  
  编译时类型检查 Compile time type checking   
  Arrow 函数 (类似 C# 的 Lambda 表达式)  

### 安装
  这里选用Node.js包管理器（npm）  

    npm install -g typescript  

  安装完成后，可使用TS编译器，名称为tsc，可将编译结果生成js文件。  
  编译TS文件，使用命令：

    tsc filename.ts  

  编译成功后，会在同意目录下生成一个同名js文件。

### 类型批注  
  提供静态类型以在编译时启动类型检查，对于基本类型的批注是number,bool,string,弱或动态类型的结构是any类型。
  类型批注可以被导出到一个单独的声明文件以让使用类型的已被编译为JavaScript的TypeScript脚本的类型信息可用。批注可以为一个现有的JavaScript库声明。  
  当类型没有给出时，TypeScript编译器利用类型推断以推断类型。如果由于缺乏声明，没有类型可以被推断出，那么它就会默认为是动态的any类型。  

    function area(shape: string, width: number, height: number) {
    var area = width * height;
    return "I'm a " + shape + " with an area of " + area + " cm squared.";
    }
    document.body.innerHTML = area("rectangle", 30, 15);  

### 接口  
  接口可以作为一个类型批注，创建一个interface.ts文件  

    interface Shape {
    name: string;
    width: number;
    height: number;
    color?: string;
    }
     
    function area(shape : Shape) {
        var area = shape.width * shape.height;
        return "I'm " + shape.name + " with area " + area + " cm squared";
    }
     
    console.log( area( {name: "rectangle", width: 30, height: 15} ) );
    console.log( area( {name: "square", width: 30, height: 30, color: "blue"} ) );


### 箭头函数表达式   （lambda表达式）  
   lambda表达式()=>{something}或()=>something相当于js中的函数，好处是可以自动将函数中的this附加到上下文中。
   也就是在在普通的function(){}中this对象无效，而改成()=>就有效。

### 类  
   支持集成了可选的类型批注支持的ES6的类  

    class Shape {
    area: number;
    color: string;
    constructor (name: string, width: number, height: number ) {
        this.area = width * height;
        this.color = "pink";
    };
    shoutout() {
        return "I'm " + this.color + " " + this.name +  " with an area of " + this.area + " cm squared.";
    }
    }
    var square = new Shape("square", 30, 30);
    console.log( square.shoutout() );
    console.log( 'Area of Shape: ' + square.area );
    console.log( 'Name of Shape: ' + square.name );
    console.log( 'Color of Shape: ' + square.color );
    console.log( 'Width of Shape: ' + square.width );
    console.log( 'Height of Shape: ' + square.height );

   构造器（constructor）中参数的作用域是局部变量，所以编译时，会报错，需要添加public修饰符。  
   
### 继承  
   继承一个已存在的类并创建一个派生类，继承使用关键字extends  

    class Shape3D extends Shape {
        volume: number;
    constructor ( public name: string, width: number, height: number, length: number ) {
            super( name, width, height );
            this.volume = length * this.area;
        };
     
        shoutout() {
            return "I'm " + this.name +  " with a volume of " + this.volume + " cm cube.";
        }
     
        superShout() {
            return super.shoutout();
        }
    }
    var cube = new Shape3D("cube", 30, 30, 30);
    console.log( cube.shoutout() );
    console.log( cube.superShout() );  

   派生类Shape3D:  
   1. Shape3D 继承了 Shape 类, 也继承了 Shape 类的 color 属性。  
   2. 构造函数中，super 方法调用了基类 Shape 的构造函数 Shape，传递了参数 name, width, 和 height 值。 继承允许我们复用 Shape 类的代码，所以我们可以通过继承 area 属性来计算 this.volume。  
   3. Shape3D 的 shoutout() 方法重写基类的实现。superShout() 方法通过使用 super 关键字直接返回了基类的 shoutout() 方法。  
   4. 其他的代码我们可以通过自己的需求来完成自己想要的功能。
