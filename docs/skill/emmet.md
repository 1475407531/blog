## Emmet神器让你写HTML/CSS快到飞起

### 一、Emmet是什么
Emmet是可以快速编写HTML/CSS代码效率的文本编辑器插件，在前端开发中，编写HTML和CSS会花费很多时间，各种标签，括号，属性一大推，学习了Emmet语法规则，复杂的标签会简单化，敲起代码爽到飞:smile:下面是总结常用的一些Emmet语法。

### 二、Emmet语法

#### HTML语法

1、 **初始化HTML文档** 
输入 **`html:5`** 敲击回车，见证奇迹啦,出现了html文件的基础结构，好神奇，好高效！
``` html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
    </head>
    <body>
        
    </body>
    </html>
```

2、**添加id（#）、class（.）、属性（[]）和文本（{}）**

举例输入 **`a.link#foo{跳转链接}[href=#]`** 回车,结果如下：
``` html
    <a href="#" class="link" id="foo">跳转链接</a>
```

3、**嵌套子节点（>）、兄弟节点（+）、上级节点（^）**

举例输入 **`div>ul>li^div`** 回车，结果如下：
``` html
    <div>
        <ul>
            <li></li>
        </ul>
        <div></div>
    </div>
```
如果是上上级用^^,**`div>ul>li^^div`** 回车，结果如下：
``` html
    <div>
        <ul>
            <li></li>
        </ul>
    </div>
    <div></div>
```

4、**重复（*）星号后面跟数字，表示重复标签个数**

举例输入 **`ul>li*4`** 回车，结果如下：
```html
    <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </ul>
```

5、**分组（()）,用()将组区分开**

举例输入 **`(div>h2)+(ul>li>p*2)`** 回车，结果如下：
``` html
    <div>
        <h2></h2>
    </div>
    <ul>
        <li>
            <p></p>
            <p></p>
        </li>
    </ul>
```
这里有个注意点，用分组时候，先写(),后写组内的标签内容，否则无效哦

6、**隐式标签**

不写标签名，直接声明一个带类的标签，即可识别父类标签，举例输入 **`ul>.test*4`** 回车，结果如下：

``` html
    <ul>
        <li class="test"></li>
        <li class="test"></li>
        <li class="test"></li>
        <li class="test"></li>
    </ul>
```
隐式标签有如下几个：
- li：用于ul和ol中
- tr：用于table、thead、tbody中
- td：用于tr中
- option：用于select中

7、**编号（$）**

举例输入 **`ul>.test$*4{测试$}`** 回车，结果如下：
``` html
    <ul>
        <li class="test1">测试1</li>
        <li class="test2">测试2</li>
        <li class="test3">测试3</li>
        <li class="test4">测试4</li>
    </ul>
```
**$代表一位数，数字是默认是从1开始递增，如果用@定义从什么数字开始，就从定义的数字开始递增**

举例输入 **`ul>.test$*4{测试$@3}`** 回车，结果如下：
``` html
    <ul>
        <li class="test1">测试3</li>
        <li class="test2">测试4</li>
        <li class="test3">测试5</li>
        <li class="test4">测试6</li>
    </ul>
```

#### CSS缩写语法

1、单位

- **p 表示 %**
- **e 表示 em**
- **r 表示 rem**

- 命令：`w100` 结果： 默认单位px

``` css
    width: 100px;
```

- 命令：`w100p` 结果：
``` css
    width: 100%;
```

2、颜色
- 命令：`c#3` 结果：
``` css
    color: #333333;
```

- 命令：`c#e0`   结果：
``` css
    color: #e0e0e0;
```

- 命令：`c#fc0`   结果：
``` css
    color: #ffcc00;
```

#### Emmet在HTML与CSS中的应用

1、命令：**link**

输入 **`link`** 回车，结果如下：
``` html
    <link rel="stylesheet" href="">
```

2、命令：**script:src**

输入 **`script:src`** 回车，结果如下：
``` html
    <script src=""></script>
```

3、命令：**img**

输入 **`img`** 回车，结果如下：
``` html
    <img src="" alt="">
```


想要详细地学习Emmet，[点击学习地址](https://docs.emmet.io)