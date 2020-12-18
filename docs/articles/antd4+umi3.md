## Antd4+umi3框架入门教程

### Ant Design介绍

<https://ant.design/index-cn>

**Ant Design是基于React实现的一套组件库。**组件（component）到底是什么东西？

如果你经常浏览各种网站，就会发现不管网页的主题是什么，通常都会使用一些重复出现的构件，比如日历、表格、表单、菜单、卡片、导航栏等等。这些构件的功能和外观都很类似，只是在一些细节的地方，根据需要做了定制。它们就叫做组件，一张完整的网页，可以看做是不同功能的组件的集合。

### React 介绍

<https://react.docschina.org/>

React 是 Facebook 公司开发推出的一套**前端开发框架**，是目前全世界最流行的前端框架。它的核心理念是将网页应用看成一个组件构成的状态机（state machine），状态的变化导致了 UI 的变化。

Ant Design 是基于 React 开发的。要使用 Ant Design，必须学会 React。

### Umi介绍

<https://umijs.org/>

Umi，中文可发音为乌米, 是蚂蚁金服体验技术部推出的编译打包工具。React 组件使用的是 JSX 语法和很多新的 ES6 语法，浏览器不支持。另外，不同的组件脚本必须打包在一起，浏览器才能加载。umi，封装了编译步骤，包括了很多开发时的有用工具。只要你写好 React 代码，接下来 umi 就会把它处理为生产代码。

### 一、初始化项目
#### 开发环境
1、首先安装[NodeJs](https://nodejs.org/en/)。NodeJS 是一个 JS 执行环境，umi 基于 JS 编写，并且需要在你的开发机上运行，所以依赖于它。安装完成，执行下面的命令确认是否安装成功
``` js
    node -v
    npm -v
```
> 在 umi 中我们采用了一些 NodeJS 的新特性， Umi 3 需要 Node 10.13 或以上,请确保你的 NodeJS 版本大于等于 **10.13**。

2、安装umi依赖

首先，新建项目文件夹，然后初始化**package.json**，存放项目信息和配置等信息的文件
``` js
mkdir antdumi && cd antdumi
npm init -y
```
上面命令中，参数 **-y** 表示对 npm 要求提供的信息，都自动按下回车键，表示接受默认值。

接着，安装 **umi** 的依赖。
``` js
npm install umi --save-dev
```
安装完成之后你会发现 **package.json** 中多出了一项 **devDependencies** 的配置。这是由于在上面命令中，参数 **--save** 可以让依赖信息保存到 **package.json** 中，这样其它开发者下载代码后就只需要执行 `npm install` 后就会自动安装项目依赖的包。<br>
另外项目中还多出了一个 **node_modules** 的文件夹，它包含了大量的内容。里面存放的是项目依赖的包，umi 的代码也是被下载并安装到其中的。如果你想要了解更多，可以参考 [npm 的文档。](https://docs.npmjs.com/)

#### 创建第一个hello world页面
1、在 **umi** 中，大量的使用了**配置和约定**来帮助你快速开发代码。首先，我们先来创建配置文件。配置文件被约定为 **config/config.js**。配置可参考umi的[文档](https://umijs.org/)

**config/config.js** 中初始化的内容如下：
``` js
    export default {

    }
```
2、首先在项目里创建**src**目录，用来存放项目除了配置以及单测以外的主要代码。

在 umi 中，约定的存放页面代码的文件夹是 **pages**，是复数，不过如果你喜欢单数的话你配置项中你可以添加 **singular** 为 **true** 来让 **page** 变为约定的文件夹。在本课程中我们使用单数来作为约定目录。所以你需要修改配置文件为：
``` js
    export default {
        singular： true,
    }
```
3、在page文件下创建HelloWorld.js文件，代码如下：
``` js
    export default () => {
    return <div>hello world</div>;
    }
```
4、下面通过umi启动代码了，在**package.json**中的**scripts**里面添加启动命令和构建代码命令：
``` js
    "scripts": {
        "dev": "umi dev",
        "build": "umi build"
    }
```
5、等项目运行起来，在浏览器中输入，**http://localhost:8000/helloworld**(端口可能因为被占用或者其他原因不同，按照实际输入),然后将会看到显示啦

**在 umi 中，你可以使用约定式的路由，在 page 下面的 JS 文件都会按照文件名映射到一个路由，比如上面这个例子，访问 /helloworld 会对应到 HelloWorld.js。也可以在配置文件config/config.js中配置**

### 二、React创建第一个组件
#### 组件定义
组件允许将UI分为独立可服用的代码片段，并对每个片段进行独立构思。组件从概念上类似于JavaScript函数。它接受任意的入参（即"props"），并返回用于描述页面展示内容的React元素。在React中我们使用更正式、更通用的**ES6的class**来定义组件

#### React组件语法
- 组件名称必须以大写字母开头
- 继承React.Component基类，重写render方法返回需要展示在屏幕上的视图层次结构，用于输出
- 组件内部状态： `this.state`（state可更新）
- 组件参数传值：`this.props`(props只读性)

#### JSX
jsx是一个JavaScript的语法扩展，JSX可以很好地描述UI应该呈现出它应有交互的本质形式。

#### jsx语法
- 标签必须闭合，点标签用/闭合
- 顶层只有一个标签
- HTML原生标签使用小写、自定义的组件标签首字母要大写
- 允许js和html混写在一起，用{}进入js上下文

注意：
1、因为JSX语法上更接近JavaScript而不是HTML，所以JSX语法中使用`cameCase`（小驼峰明明）定义属性的名称，而不使用HTML属性名称的命名约定。
例如：JSX里的`class`变成了`className`
2、为了便于阅读，我们会将jsx拆分为多行。同时将内容包裹在括号中，这样可以避免遇到自动拆入分号的陷阱。
  
``` javascript
import React from 'react';

class ShoppingList extends React.Component {   
    constructor(props)  {
        super(props);
        this.state = {
            count: 0
        };
    }
    render() {
        return (
            <div className="wrapper">
                <h2>Shopping List for {this.props.name}</h2>
                <ul>
                    <li>Instagram</li>
                    <li>WhatsApp</li>
                    <li>Oculus</li>
                </ul>
                <p>{this.state.count}</p>
                <button onClick={() => this.setState({count: 3})}>点击增加</button>
            </div>
        );
    }
}
export default ShoppingList;
```

#### React组件生命周期
- `componentDidMount`：组件挂载后自动调用
- `componentWillUnmount`：组件卸载前自动调用
- `componentDidUpdate`：UI每次更新后调用

### 三、使用Ant Design组件

通过前面的步骤，已经搭建完成了脚手架，并且了解了React的基本概念，下面来使用Ant Design组件。

#### 引入antd

Ant Design 是一个服务于企业级产品的设计体系，组件库是它的 React 实现，antd 被发布为一个 npm 包方便开发者安装并使用。



1、添加 @umijs/preset-react 插件

umi 是一个可插拔的企业级 react 应用框架，它的很多功能都是通过插件实现。尤其是 umi 官方的 [@umijs/preset-react](https://umijs.org/) 这个插件集成了常用的一些进阶的功能，执行安装代码进行安装：

``` js
npm install @umijs/preset-react --save-dev
```
2、配置 @umijs/preset-react 插件

使用了脚手架，Ant Design已经自带了，不需要自己安装了

``` js
    export default {
        antd: {},
        routes: [{
            path: '/',
            component: './HelloWorld',
        }],
    }
```
3、使用antd
在HelloWorld.js页面引入antd组件，首先在头部引入Card组件

``` js
    import { Card } from 'antd';
```
然后我们按照antd组件的API添加，[组件API](https://ant.design/components/overview-cn/)



想要详细地学习Antd4+umi3，[点击学习地址](https://www.yuque.com/ant-design/course/lsoh4c)
