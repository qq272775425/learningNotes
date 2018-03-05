优点：轻量级 高效率 上手快 简单易学 文档全面而感觉
功能 渲染模板 模块化 拓展功能路由 ajax 
前置知识 
	node及npm操作 
	html css js基础 
	js es6 语法 

轻量级前端界面框架 2016年10月份发布2.0版本 更强大 更快捷

数据渲染 数据同步 
组件化 模块化
其他功能 路由 ajax 数据流

学习资源 官网 cn.vuejs.org

vue 事例话对象
在引入vue.js 后在全局中会有一个vue类 在new Vue 之后得到一个vue对象 vue是构造函数 内部是函数参数

el 将组件对象装载到什么位置 可以通过各种选择器选择标签
templete 是我们的指令或其他组件的片段 HTML代码 模板
data：{} 通过data引入数据data中的数据会被代理到实例对象可以通过 事例化对象.变量去调用 并可以在templete中通过{{}}进行调用

项目开发中 
首先在body中引入根组件 形成组件树

Vue生命周期 钩子 2.0版本比1.0版本省略一些钩子 节点调用函数 生成 销毁之类的

如何实现vuejs的跟组件 以及组件之间的相互关系


数据渲染
在main。js中通过import Vue form 'vue'
import Vue form 'vue'
new Vue ({
	el:'#app',
	template:"<p>hello world{{world}}</p>",
	data:{
		world:'hello world'
	}
})

数据放在data中 渲染通过双花括号{{}}放在template中

//注册全局组件
import Vue form 'vue'
Vue.component('my-header',{
	tenplate:'<p>this is header{{}}</p>'
	data{
		header:'haha'
	}
})


new Vue ({
	el:'#app',
	template:"<p>hello world{{world}}</p>",
	data:{
		world:'hello world'
	}
	components：{
		'my-header':我是
	}
})


组件注册 引入 通过层层嵌套形成组件数进行组件树 页面布局 

避免给data进行引用赋值，直接引用data并进行赋值会导致所有组件的data值都相同且改变一个data值其他的数值也跟着改变 解决办法： 在组件赋值时返回data 


给data进行引用赋值
data：{
	f:2,
	d:3
}

解决方法 这样声明数据时当我们改变第一个组件的数据时不会影响第二个组件的数据
data：function(){
	return{
		f:2,
	}	d:3
}
data:(){ //function可以省略
	return{
		f:2,
	}	d:3
}


vue 基本概念 
	全局api
	实例选项
	实力属性、方法
	指令 
	内置组件 
全局api 
	Vue.extend()拓展vue构造器的方法
	Vue.set()设置全局vue属性
	vue.components() 添加全局组件
	Vue.use() 使用注册插件

实例选项 在创建vue实例对象时可使用的具有功能性的项目 
	数据相关 
	dom相关
	生命周期钩子
	el
	data
	compontents

实例的属性方法
还提供了一些方法
vue.$data
vue.$on('click',function(){
	
})

指令 以v-开头的一堆乱遭的方法
写在模板里面，通过模板与组件数据进行交互的重要方法 指令还可以包含指令参数 
指令实现了实例的属性和页面元素之间的交互
例如v-on：click='' 所有指令都可以通过：参数的方式实现指令参数v-on：keydown.enter=''


内置组件 
	keeplive 
	components
可以直接使用vue的内置组件实现


vue的基本用法 
访问文件为index.html的主页文件
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<div id="app"></div> //根组件的挂在位置
</body>
</html>



main.js文件 加载跟组件

import Vue form 'vue'
import app form './App' 这个app组件通过import方法从当前目录下的app.vue文件引入,作为根组件进行渲染           
new Vue({  //事例话一个跟组件
	el:'#app',  对象装载的位置
	render:h => h(App) //2.0版本需要使用rander方法渲染外部引入的app组件 									"=>"这个是es6中的写法 
						h => h(App) === function (h){
											return h(App)
										}
})

模板渲染：
当data中有键值对的时候 
data(){
	return{
		hello:'world';
	}
}
可以通过{{hello}}的方式 将data中声明的变量渲染到页面，会在指定位置显示出变量的值
还可以通过在标签内部添加v-html="hello"的方式’进行渲染<p v-html = "hello"></p>
还可以通过在标签内部添加v-text="hello"的方式’进行渲染<p v-text = "hello"></p>
区别 v-html 会将data 中的数据通过html节点方式解析呈现
     v-text 会将data 中的数据通过文本方式解析呈现
{{}}中可以传入简单表达式 {{num + 1}}{{statues ? 'success' : 'fail'}}

列表渲染 v-for