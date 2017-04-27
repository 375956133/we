## 混合App

- 讨论
- 移动app与 移动web,网站!
- web前端!
- 移动端的网页

- 原生开发QQ,微信: java
- 原生js开发网站,jquery


- 什么混合app
- java,javascript,html,css还开发应用
- 通过前端技术来开发的App
- 微信!,朋友里打开的文章其实是一个个网页!
- 微信里时有内置浏览器 - 可以自动打开一个网站!
- www.baidu.com

- 网页- 浏览器
成本!
现在我要做微信!
苹果版本的微信oc，android版本的微信 java
- 至少要招两个人!
跨平台!
写一个网页，可以把这个网页变为app

- 微信,qq,京东
- 在混合app中我们前端要做什么

- react

## 混合App
- 内部的页面全部用html,css,js来写!
- 然后通过已有工具，把那些html,css,js内置到  特定浏览器里
- hbuilder
    + 能够把我们写的html,css,js打包成一个apk文件，、
    + 只要把这个文件发送到手机上，点击就能直接安装上了

- 还有一种混合App，是用原生开发,有部分内容是用网页做的!
    + 比如说: 天猫: 促销活动

- 如果是网页，网页变化，需要重新安装(只需要刷新一下!)

### *做混合，还是用前端的技术做开发!,最后只是用工具将前端写的代码打包成一个安装包*
React-Native 是做App开发的,是用前端的技术来做App
- 移动App端
- RN

React 是web端的框架
- jquery 是前端操作dom的库! //var $ = document.querySelector $()
- angular是什么
- vue 就是

- 操作dom频率越来越来少了!
- 数据绑定/数据驱动!

- hao123,全是a标签!
- jquery,angular,react...
- 禁用javascript
- 为什么要学，为什么要有jquery
    + 操作dom方便!

假如页面上就只有一个 button按钮，要注册一个点击事件，弹出helloworld
+ 需求!


页面上有好多,好多表单(10个input)，要用ajax提交，
<!--  -->
jquery

- 有一天，前人发现jquery也不够用了
- 样式变了，js代码还要改!
- <div class="tmp">{{name}}</div>
- <p>{{name}}</p>



## es6

## webpack
- 工具 -> 就是让我们开发者不需要在html中引入太多的js代码!
- 安装:`npm install -g webpack`
- 可以把js代码合并在一起
- 可以像node一样去写js代码,通过module.exports暴露对象
- 在别一个js文件中通过require来得到这个对象

- webpack不仅仅可以把多个js合并一起，还能把css合并进行js中

- 要把less转换为css

- webpack 本身只能合并js代码
    + 我们可以让它的功能扩展一下,使其他能够合并css代码到js中!
    + 我们要单独写个js文件:  webpack.config.js

## webpack.config.js
> 在当前项目中新建 这个文件

## css-loader style-loader
- `npm install css-loader style-loader`
- style-loader是用来把css插入到页面的style标签中!
- css-loader是用来处理css中特殊语法: @import 'xx.css'
- css-loader把处理后的css代码交给 style-loader处理

```js

// var str = '#btn{
//   width: 100px;
//   height: 39px;
//   background: #f64d4d;
//   border: none;
//   outline: none;
//   border-radius: 4px;
//   color:#fff;
//   font-size: 16px;
// }'

// var styl = document.createElement('style')
// styl.innerHTML = str
// document.body.appendChild(style)
```

## less-loader
- `npm install less-loader`
   *注意:下载less-loader有个依赖自动下载不下来,需要单独下载*:
     `npm install less`

- 这个包能够把less文件中的内容转换为css代码!
- 改一下webpack.config.js中的代码

```js
     {
       test: /\.less$/,
       // less-loader是用来将less请求转换为css的
       loader: 'style-loader!css-loader!less-loader'
     }
```

### babel-loader
> es2015 就是 es6

```js
  {
      test:/\.js/,
      loader: 'babel-loader'
  }
  // babel-loader这个包会固定的去读取一个文件, .babelrc 这个文件
  // 在webpack.config.js同级新建 .babelrc 这个文件
```
```js
// .babelrc
{
  // es2015对应一个第三方包: npm install babel-preset-es2015
  // babel-preset-es2015 是用来把es2015代码转换为es5
  // react: npm install babel-preset-react
  // babel-preset-react 作用是把react语法转换为js语法!
  "presets":["es2015","react"]
}
  
```
*注意:* 在下载`babel-loader` 时，不会自动下载自身的依赖包: `babel-core`
使用babel-loader需要下载的包:至少
`npm install babel-loader`  
`npm install babel-core`
`npm install babel-preset-es2015`

## react

```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Document</title>
  </head>
  <body>
    
  </body>
  </html>
<script src="./lunbo.js"></script>
<script src="./fenye.js"></script>
<script src="./cart.js"></script>
<script src="./cart.js"></script>
<script src="./cart.js"></script>
<script src="./cart.js"></script>

```

- 模块化

- 组件! - bootstrap
- 组件化开发!
- 组件开发除说js之外，还侧重于html,css

- vue

<!-- msdn -->

## react
- ReactDOM.render
   把div这种东西插入到html中

### react中的组件怎么写
- 3步
- 1. 组件写在一个单独的js(.jsx)文件中,需要引入 `react`
  + 后缀名并不重要
- 2. 用class申明一个构造函数， 要继承自 `react.Component`
  + render() 必需要写
- 3. 暴露出去

- 最终在main.js中引入我们要用的组件，调用ReactDOM.render将组件中的标签
- 渲染到html中

## 相关链接
- 玩的心态去学习!
- class function

- 英文! 勇敢!
- http://reactjs.cn/react/docs/getting-started-zh-CN.html
- http://reactjs.cn/react/
- https://facebook.github.io/react/
- http://react-china.org/
 
## 在公司里做后台管理的项目!

--save
--save-dev