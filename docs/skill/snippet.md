## 创建自己的snippets，让编码效率翻倍

### snippets是什么
code snippets，也叫作代码模板，可以快速生成代码片段。平时前端工作中都需要用到固定模式的代码片段，我们只需要自定义代码片段，用关键字加快捷键的方式就可以快速生成，不需要手动编写或者复制固定代码。比如一个HTML文件固定的代码：
``` html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge, chrome=1">
        <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0"> 
        <title></title>
    </head>
    <body>    
        <div></div>   
    </body>
</html>
```
再比如vue文件固定结构代码：
``` html
<template>
    <div class="">vue文件</div>
</template>

<script>
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';

export default {
    //import引入的组件需要注入到对象中才能使用
    components: {},
    data () {
        //这里存放数据
        return {

        }
    },
    //生命周期 - 创建完成（可以访问当前this实例）
    created () {

    },
    //生命周期 - 挂载完成（可以访问DOM元素）
    mounted () {

    },
    destroyed () {}, //生命周期 - 销毁完成
    //方法集合
    methods: {

    }
}
</script>
<style scoped lang='scss'>
    
</style>
```

### 如何设置使用

像上面这些固定的代码片段，我们就可以设置为snippet模板，使用时快速生成想要的模板代码片段，节约重复代码开发时间，提高工作效率，下面我以VSCode编辑器为例来设置并使用。

1、选择文件 > 首选项 > 用户代码，打开**命令窗口**，输入snippet（按快捷键Ctrl+Shift+P）,通过候选栏中的选项进入目的语言的代码段设置文件。

2、填写snippets
设置文件头部通过一个块注释讲解了snippets的文法。下面设置一个html代码段模板
``` javascript
{
	// Place your snippets for html here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same ids are connected.
	// Example:
	// "Print to console": {
	// 	"prefix": "log",
	// 	"body": [
	// 		"console.log('$1');",
	// 		"$2"
	// 	],
	// 	"description": "Log output to console"
	// }

	"Print to console": {
		"prefix": "html",
		"body": [			
			"<!DOCTYPE html>",
			"<html lang=\"en\">",
			"<head>",
			"    <meta charset=\"utf-8\">",
			"    <meta http-equiv=\"X-UA-Compatible\" content=\"IE=edge\">",
			"    <meta name=\"viewport\" content=\"width=device-width,initial-scale=1.0\">",
			"    <title>$1</title>",
			"</head>",
			"<body>",
			"    <div class=\"$2\">",
			"    </div>",
			"</body>",
			"</html>"
		],
		"description": "生成HTML文件模板"
	}
}
```

定义好了html代码片，下面我们新建一个.html文件使用看一下效果，在新建的文件中，**输入html**然后回车，就会出现下面的代码片段了：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title></title>
</head>
<body>
    <div class="">
    </div>
</body>
</html>
```
光标会在title这里，输入标题，按**Tab**键，光标会跳到body下div的class这里提示输入。这样子一个自定义html模板代码片段就定义完成了。

同样方法再添加一个vue的模板代码
``` javascript
{
	// Place your snippets for vue here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same ids are connected.
	// Example:
	// "Print to console": {
	// 	"prefix": "log",
	// 	"body": [
	// 		"console.log('$1');",
	// 		"$2"
	// 	],
	// 	"description": "Log output to console"
	// }
	"Print to console": {
        "prefix": "vue",
        "body": [
            "<!-- $1 -->",
            "<template>",
            "    <div class=\"$2\">$5</div>",
            "</template>",
            "",
            "<script>",
            "//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）",
            "//例如：import 《组件名称》 from '《组件路径》';",
            "",
            "export default {",
            "    //import引入的组件需要注入到对象中才能使用",
            "    components: {},",
            "    data () {",
            "        //这里存放数据",
            "        return {\n",
            "        }",
            "    },",                    
            "    //生命周期 - 创建完成（可以访问当前this实例）",
            "    created () {\n",
            "    },",
            "    //生命周期 - 挂载完成（可以访问DOM元素）",
            "    mounted () {\n",
            "    },",            
            "    destroyed () {}, //生命周期 - 销毁完成",
			"    //方法集合",
            "    methods: {\n",
            "    }",
            "}",
            "</script>",
            "<style scoped lang='scss'>",
            "$4",
            "</style>"
        ],
        "description": "Log output to console"
    }
}
```
vue为关键字，快去尝试吧！

3、snippets语法详解
snippets有三部分组成：
- **prefix**（必须）：前缀，触发条件关键字，像上面例子，输入**html**时会触发代码片生成
- **body**（必须）：主体，数组形式定义
- **description**（非必输）：描述

### 总结
文章只举了一个例子，我们还可以自定义很多自己需要的代码段。学习更多技巧，少些重复代码，提高编码的效率，让我们有更多的时间优雅地解决更多的事情:smile:

想要详细地学习snippets语法，[点击学习地址](https://code.visualstudio.com/docs/editor/userdefinedsnippets)
