# vue-todo-app notes



- 项目介绍

  最终效果，功能实现

  使用技术

- 项目来源，步骤

  链接

- html and css 

  遇到的困难

- vue （重点）

  framework 整体逻辑

  核心功能详解

- 总结





## 项目介绍

为熟悉vue框架基本功能，使用vue实现简易的todo-app，具有添加、删除、修改状态，筛选显示条目的功能

界面效果如图所示

tools ：html, css, js, vue-cli

editor : vs-code 

deploy : render.com

[live demo](https://vue-todo-qb20.onrender.com/)

<img src="C:\Users\Gamma\AppData\Roaming\Typora\typora-user-images\image-20210821101532507.png" alt="image-20210821101532507" style="zoom:50%;" />



## 项目来源

b站@峰华端工程师

[Vue 3.0 实战，开发基于 Composition API 的 Todo Web App]([[完整版]Vue 3.0 实战，开发基于 Composition API 的 Todo Web App_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1wy4y1k7Lr))

[github源码](https://github.com/zxuqian/vuejs-examples)

不过我没有用composition API, composition API 是vue3新出的，相当于是option API的优化版本，主要优点在于提高代码的可读性，解决逻辑复用的问题。

二者的使用并不矛盾，由于我一开始先接触option API，且还不熟悉，就先用它写了。等后期再学习composition API的用法。



### 主要步骤

@峰华端工程师 给的视频非常简短，但明确列出了项目从idea到最终实现的几个关键步骤，非常具有指导意义。

- 寻找项目灵感
- 创建 vue 项目
- 编写 html 结构
- 编写 css 样式
- 抽离组件
- 处理事件与数据
- 总结 



## 项目灵感

github trending, explore

dribbble - 设计师网站

codePen 



## 界面实现

> html 和 css， 写的时候才知道自己有多菜



### HTML

#### 分析结构（很重要）

``` html
<container>
    <h1> Welcome Message </h1>
    <div class="todo-add"></div>
    <div class = "todo-filters"></div>
    <div class="todo-list">
        <div class="todo-item"> content </div>
    </div>
</container>
```



### CSS

#### search bar 的效果

[Simple Search Bar (codepen.io)](https://codepen.io/huange/pen/rbqsD)

用一个`container`包含`input`和`icon`，`flex`布局，`input`宽度100%，`icon` position设为absolute调整位置

``` html
<div class="search">
     <input type="text" class="searchTerm" placeholder="What are you looking for?">
     <button type="submit" class="searchButton">
        <i class="fa fa-search"></i>
     </button>
</div>
```

``` css
.search{
    position: relative;
    display:flex;
}
.searchTerm{
    width:100%;
}
.searchButton{
    position: absolute;
    right:0;
    top: 50%;
    transform:translate(0,-50%)
}
```



#### custom checkbox (有点复杂)

**Step 1: Hide** the input element.

**Step 2:** Add an extra **span** element and apply your custom style by creating a class.

**Step 3:** Use ::before or ::after pseudo element

[Costumizing CheckBox with pure CSS. (codepen.io)](https://codepen.io/BrahmaUI/pen/WgOGQz)



# Vue

vue app 的结构是由 component 搭建起来的

In Vue, a component is essentially an instance with pre-defined options. 

- component
  - root component 
  - component property
  - 
- 数据流
- 事件处理
- 

## component



[ ] register

[ ] root componet

[ ] single file component usage 



[ ] properties







### vue app的起点

vue app 是由一个个组件构建起来的，用根组件(`root component`)作为参数创建一个vue app，app创建之后需要挂载到DOM元素中，而根组件就作为渲染的起点。

使用逻辑如下

``` js
const RootComponent = {
  /* options */
}
const app = Vue.createApp(RootComponent)
const vm = app.mount('#app')
```

把大象装进冰箱总共分为几步？

- root component
- create app
- mount the app into `<div id="app"></div>`

> 当使用vue-cli时，创建项目后这些会自动生成，components 会单独放到一个文件夹，使用方式转变为模块化的 import / export



### Single File Component (更成熟的组件组织方法)

SFC (aka `.vue` 文件 )，就是一个 `component`， 文件结构包含三个部分：

- template
- script
- style

它将对`component`的全部定义，整合到一个文件中。通过自动的预编译，生成标准的 `js module` ，也就是说能够作为模块 `import` 到其他文件中。



``` javascript
import MyComponent from './MyComponent.vue'

export default {
  components: {
    MyComponent
  }
}
```



### component properties



### component lifecycle hooks



### data flow 



### event handling 

