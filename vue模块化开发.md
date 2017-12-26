[TOC]
# VUE模块化开发

## 一、模块化开发

### 1.vue-router模块化开发
	npm install vue-router -S //生产依赖

#### 1.1 编辑main.js

#### 1.2 编辑App.vue

#### 1.3 创建router.config.js文件进行路由匹配

### 2.关于ajax请求即axios的模块化开发
	npm install axios -S

	使用axios的两种方式：
		方式1:在每个组件中引入axios(这样太过麻烦，不太好)
		方式2:在入口文件main.js中进行全局引用，并添加到Vue类的原型中

	注：（axios不太成熟，它不是作为全局的来使用，不是全局的插件，不像vue-router）

### 3.为自定义组件添加事件
	修饰符.native

## 二、Element UI

### 1.简介
	element ui是饿了么团队提供的一套基于vue2.0的组件库,可以快速搭建网站，提高开发效率

	ElementUI PC端
	MintUI 移动端

[pc端的库](http://element.eleme.io/#/zh-CN)
[移动端的库](http://mint-ui.github.io/#!/zh-cn)

### 2.快速上手

#### 2.1 安装element.ui	
	npm install element-ui -S

#### 2.2 在main.js中引入并使用组件
```
	//这种方式引入了elementUI中所有的组件
	import elementUI from 'element-ui'
	import 'element-ui/lib/theme-default/index.css'

	Vue.usr(elementUI)

```

#### 2.3 在webpack.config.js中添加loader
	css样式和字体图标都需要有相应的loader进行加载，所以我们需要style-loader、css-loader file-loader 


#### 2.4 使用组件

#### 2.5 使用less
	安装loader,需要两个loader:less和less-loader
	npm install less,less-loader -S

### 3.按需引入组
	

#### 3.1 安装babel-plugin-component
	npm install babel-plugin-component -D

#### 3.2 配置.bebelrc文件
	"plugins":[
		[component:
			[
				{
					"libraryName": "element-ui",
      				"styleLibraryName": "theme-default"
				}

			]
		]
	]

#### 3.3 只引入需要的插件

`遗留问题：babelrc到底是干嘛用的`


## 三、自定义全局组件(插件)

	全局组件（插件）：是指可以在main.js中使用vue.use()进行全局引用，然后在其他组件中都可以直接使用了，如vue-router
		import VueRouter form 'vue-router';
		Vue.use(VueRouter)

	普通组件（插件）：是指每次使用时都需要引入，如axios
	 	import axios form 'axios';

### 1.如何使用
	vue init webpack-simple component-demo


## 四、Vuex 用于复杂组件之间的数据传递(重点及难点)

### 1.简介
	Vuex是一个专为Vue.js应用程序开发的状态管理模式，采用集中式存储管理应用所有组件的状态，并以相应的规则保证状态以一种可预测的方式放生变化。
	简单来时，就是用来集中管理数据的，类似于react中的Redux,都是基于Flux的前端状态管理框架

### 2.基本用法

#### 2.1 安装vuex
	 npm i vuex --save

#### 2.2 创建store.js文件，在main.js中导入并配置store选项

#### 2.3 编辑store.js文件
	vuex的核心就是store（仓库），相当于一个容器，一个store实例中包含以下的属性和方法：
		state 定义属性（状态数据）
		getters 用来获取属性的
		actions 定义方法（动作）
		commit 提交变化，修改数据的唯一方式就是显式的提交mutations
		mutations 定义变化

		注：不能直接修改数据，必须显示的提交变化，目的是为了追踪到状态的变化

#### 2.4 编辑App.vue
	在子组件中访问store对象的两种方式：
		 方式1:通过this.$store访问
		 方式2:通过mapState,mapGetters,mapActions访问，vuex提供了两个方法：
		 	mapGetters 获取state
		 	mapGetters 获取getters 属性（数据）
		 	mapActions 获取actions 方法（动作）

### 3.更好的组织Vuex项目结构
	|-src
		|-store
			|-index.js
			|-getters.js
			|-actions.js
			|-mutation.js
			|-modules //分为多个模块，每个模块都可以拥有自己的state，getters,actions,mutations
				|-user.js
				|-cart.js
				|-goods.js
				|-...


## 五、综合案例

### 一、准备工作

#### 1.初始化项目
	npm vue init webpack my-vue-project
	cd my-vue-project
	npm install
	npm install style-loader less less-loader -D
	npm install axios vuex -S
	npm run dev

#### 2.项目资源
	|-reset.css
	|-data.json

#### 3.创建目录结构
	首先清楚项目中的部分内容

	创建如下的目录结构：
		
		|-static
			|-css
				|-reset.css

#### 4.配置API接口，模拟后台数据
	使用express框架启动一个node服务器，配置API接口，模拟后台的数据

	测试api:
		http://localhost:8080/api/rows

### 二、项目整体结构开发
	
	











	