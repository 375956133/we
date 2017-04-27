## app

## react有可能会和jquery混用
- 是用的jquery插件
- vue很强大,react很强大!
- 必需引用jquery

### webpack 中将引入的包里的对象变为全局变量
- 在plugins里再添加一个插件

```js
// webpack.config.js
   plugins:[
    // 以jquery为示例
    new webpack.ProvidePlugin({
    // key就是全局变量名,value就是包名
    // 有些jquery插件用的是jQuery对象
    // 有些用的是$对象
    jQuery: 'jquery',
    $:'jquery'
    // 如果是其他包也是类似写法！
    // xx: './a.js'
   })
  ]
  // ./a.js
  module.exports = {a:1}
```
<!-- // vue-cli -->

## 如果要打包vue的项目(用单文件组件的形式)

```js
    // webpack.config.js
    module:{
    loaders:[
      {
        test:/\.vue$/,     // 字体// 图片, css,js 
        loader:'vue-loader' // 是用来处理.vue后缀的文件
        // npm install vue-loader vue-template-compiler css-loader --save-dev
      }
    ]
  }
```


## 在react中对标签和属性有限制
- 参考: `https://facebook.github.io/react/docs/dom-elements.html`
- className, htmlFor 
- colSpan rowSpan

## 下午React 和 webpack 补充!

```js
  extract-text-webpack-plugin
  ExtractPlugin.extract({
        use: 'css-loader'
  })

```

```js
  //new webpack.optimize.CommonsChunkPlugin({
  //name: ['vender','mainfest']{)
  //devServer
  //port
  //contentBase
```

## react生命周期（生命周期方法/钩子!)
- constructor()//  class 自带
+ 初始化this.state的值 this.state = {}

- componentWillMount
  + new Btn 是创建组件实例,react在创建组件实例之前 会调用componentWillMount
  + 我们可以在这个方法写发请求的代码!
- render
  + return 一个标签!

- componentDidMount
  + 是在render之后执行,此时组件的标签已经在dom中存在



>说明:  
- es6创建组件的方式是定义一个class
- es5创建组件的方式是React.createClass({})
- 生命周期其实是数据及dom的变化过程!

1. getDefaultProps // defaultProps

作用于组件类，只调用一次，返回对象用于设置默认的props，对于引用值，会在实例中共享。

2. getInitialState// constructor

作用于组件的实例，在实例创建时调用一次，用于初始化每个实例的state，此时可以访问this.props。

3. componentWillMount

在完成首次渲染之前调用，此时仍可以修改组件的state。

4. render

必选的方法，创建虚拟DOM（能够优化性能!），该方法具有特殊的规则：
只能通过this.props和this.state访问数据
可以返回null、false或任何React组件
只能出现一个顶级组件（不能返回数组）
不能改变组件的状态
不能修改DOM的输出

5. componentDidMount

真实的DOM被渲染出来后调用，在该方法中可通过
this.refs
访问到真实的DOM元素。此时已可以使用其他类库来操作这个DOM。

6. componentWillReceiveProps
父组件在传递props子组件之前会调用这个方法

组件接收到新的props时调用，并将其作为参数nextProps使用，此时可以更改组件props及state。

```js
    componentWillReceiveProps: function(nextProps) {
    // nextProps是父组件即将要给子组件传递的属性
        if (nextProps.bool) {
            this.setState({
                bool: true
            });
        }
    }
```

7. shouldComponentUpdate
- 如果我们写了这个方法,当每次我们调用this.setState({})的时候
- 这个方法里还会调用这个`shouldComponentUpdate`,如果在这个方法里返回true就会继续
调用 render
如果返回false,就不执行后缀的代码，也不会render了

组件是否应当渲染新的props或state，返回false表示跳过后续的生命周期方法，通常不需要使用以避免出现bug。在出现应用的瓶颈时，可通过该方法进行适当的优化。

在首次渲染期间或者调用了forceUpdate方法后，该方法不会被调用

8. componentWillUpdate

接收到新的props或者state后，进行渲染之前调用，此时不允许更新props或state。

9. componentDidUpdate

完成渲染新的props或者state后调用，此时可以访问到新的DOM元素。

10. componentWillUnmount

componentDidMount(){
  this.state.setId = setInterval(function(){

  },1000)
}
// 当组件消失时调用
componentWillUnmount(){
  // 清除计时器
}

组件被移除之前被调用，可以用于做一些清理工作，在componentDidMount方法中添加的所有任务都需要在该方法中撤销，比如创建的定时器或添加的事件监听器。

## React props
> es6 这两个属性不能写在class内。

- Class.propTypes={//属性校验器，表示改属性必须是bool，否则报错
  title: React.PropTypes.bool,
}
- Class.defaultProps={title:'133'};//设置默认属性
- defaultProps
- this.props.children

## 虚拟dom树
- 为什么要有虚拟dom树!
- V8-js
- dom操作其实是很慢的!
- dom其实就是一个js对象, oDiv = {id:'box',innerHTML:'你好吗'}
- react 会自动计算新的div与原来的dir元素属性的区别,如果react发现只改变了innerHTML
react会修改变化的部分。

- 虚拟dom树
  + 其实就是一个js对象
  + 这个js对象的属性和dom对象的属性一致!,我们在react中修改数据里，其实先
  + 变化是虚拟dom树这个js对象，然后react会将 这个虚拟dom树对象与真的dom树对象
  做对比,只修改变化的部分!

- vue中也有虚拟dom树概念!

## mvc思想
- 不是解决的性能!,改变了代码的书写形式及结构

```html

  // index.html --- view
  <button id="btn" onclick="alert(1)"></button>
  <script src="xx.js"></script>

  constroler.js
  document.getElementById('btn')
  .onclick= showdata


  // model.js
  function showdata(){
    // 写里是对数据的操作
    // 
    alert(11) // 也有可能是发请求修改数据
  }
```

## mvvm 思想
- 自动把数据呈现到页面上去!
- 把程序的精力放在创造上!

## 相关资料链接
- [组件生命周期](http://react-china.org/t/react/1740)
- [虚拟dom树实现](https://github.com/livoras/blog/issues/13)

- [重绘与重排]
- 频繁的动画，dom操作会导致重排(浏览器重新排列并计算新的dom元素的宽高)
- 每次重排之后会重新绘制
  + 如果仅仅是改变颜色,是不会导致重排，只会导致重绘

- dom.style.width = 100px;
- var w = dom.clientWidth // 获取宽高，必然导致重排!(因为浏览器要重新计算宽高!)
- dom.style.height = 101px;

// 把样式事先写到css中，通过修改dom元素的class来更改样式!
// class 不管理写了多少样式，浏览器只重排一次!
<!-- - dom.style.color
- dom.style.backgrounColor -->

var $btn = $('.btn')
$btn.height('100px')
$btn.html()

>1、添加或者删除可见的DOM元素
2、元素位置改变
3、元素尺寸改变
4、元素内容改变（例如：一个文本被另一个不同尺寸的图片替代）
5、页面渲染初始化（这个无法避免）
6、浏览器窗口尺寸改变
clientWidth,clientHeight

## webpack 
- 把css 样式不合并到js中

### 单独提取到一个css中
>extract-text-webpack-plugin
  ExtractPlugin.extract({
        use: 'css-loader'
  })
  new ExtractPlugin('all.css')
> `npm install extract-text-webpack-plugin --save-dev `

### 把第三方包提取出来!
- 第三方包的代码很少会变
- 自己写的代码经常会变!
  + 我们是希望浏览器组件住第三方包的代码，
  + 当我们修改自己的代码时就不缓存
  `<script type="text/javascript" src="bundle.js"></script>`

  `<script src="第三方包.js"></script>`
  `<script src="自己写的.js"></script>`




## 明天RN

// Boxy theme
// MWebLite

### python 2.xx
### jdk 
### sdk 

### 晚上任务
- 安装： `npm install -g yarn react-native-cli`
- 如果感觉下载包慢的话:就设置:

```js
yarn config set registry https://registry.npm.taobao.org --global
yarn config set disturl https://npm.taobao.org/dist --global
```

- 生成基本的项目结构

`react-native init 文件夹名`

## fps
