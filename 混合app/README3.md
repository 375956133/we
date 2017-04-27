# app

## 父子组件之间传值

### 父组件给子组件传值
- 1.在父组件中，使用子组件标签时，在子组件标签的属性上添加!
  `<Child mymsg={this.state.msg}></Child>`
  就相当于给子组件实例的props属性添加了一个 mymsg属性
  `Child的实例.props.mymsg = this.state.msg`
- 2.然后在子组件Child内部就可以直接通过this.props.mymsg得到这个值
- *注意*，不仅仅是传递字符串，所有的类型都可以传递!

### 子组件往父组件传值!
- 1.需要在父组件中提供写好一个方法

```js
    getDate(msg){

    }
```
- 2.通过父组件给子组件传值的方式,把方法传递给子组件!

```html
    <Child mygetDate={this.getDate.bind(this)}></Child>
```
- 3.这样在子组件里可以直接调用2中传递过来的方法

```js
    this.props.mygetDate('可以传递任意参数')
    // 这里调用时，执行的是1中的方法
    // 在1中的方法，把参数赋值父组件的state的某个属性，这样就能在父组件的标签中使用
    // 这个数据
```
- 4.

```html
    getDate(msg){
        this.state.msg = msg
        // 更新父组件的dom
        this.setState({})
    }
    render(){
    return (<div>
            {this.state.msg}
            </div>)
    }
```


## axios
- 专门用来发ajax语法的包
- `npm install axios`
- new XMLHttpRequest()



## react路由
- 什么是路由?
- spa
- 一个页面，页面整体不刷新不跳转
- `npm install react-router-dom --save`

### react路由基本使用
- `import {HashRouter, Route} from 'react-router-dom'`

```html
    // 这个Route是写在Box中的
    <Route path="/home" component={组件}></Route>
```

### react嵌套路由

```html
    // 这个Route是写在Box中的
    <Route path="/home" component={Home}></Route>
```

```html
       
   // 这个Route写在Home组件 
   // 这里的path一定是以/home开头
    <Route path="/home/xxx" component={HomeA}></Route>
```

> history.pushState("","dd",'/liuqi.html') 
> 改变地址栏端口以后的部分，页面不会跳转

### react带参数的路由


## 相关资料
- [react路由中文文档](https://reacttraining.cn/)
- [react路由英文文档](https://reacttraining.com/react-router/)

- [json-server](https://github.com/typicode/json-server)
    + 安装: `npm install -g json-server`
    + `json-server --watch test.json --port 8091`

```html
    <!-- <h1>{{email}}</h1>
    <input type="text" v-model="email"> -->
```

## 明天webpack拓展

<html>
    <body>
        
        <ul>
            <li v-for="item in list">{{item.name}} </li>
        </ul>
    </body>
</html>

<script>
    data: ｛
    list:[]｝

    axios.get('./a.json')
    .then((res)=>{
        this.list = res.data 
    })
</script>




