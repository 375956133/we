## 组件里的一些内容 
- 1.要组件里的标签中呈现js对象的属性值
    + 有个约定: 把所有要在页面呈现的数据都放到this.state这个对象中
    + 假如在render中return 一个div,我希望在这个div中呈现一个： 你好吗?
      * a.给this.state添加一个属性: `this.state={msg:'你好吗'}`
      * b.修改那个div: `<div>{this.stage.msg}</div>`
      * 结果，html页面上就会看到 `你好吗` 三个字
    
- 2.要在input中呈现js对象的属性值
    + 和1中的约定是一致的
    + 假如组件中有个input中，我希望让input有个默认值为 `hello world`
        * a.给this.state添加一个属性： 
        `this.state = {msg:'你好吗', hl:'hello world'}`
        * b.给input添加一个 value 属性,属性值为 this.state.hl
        *注意: value=这里不要加引号,直接写大括号*
        `<input type="text" value={this.state.hl}>`
        * 结果，在html页面上就会看到input里有 `hello world` 

- 3.要给标签注册事件
    + 给标签添加相应的属性，如:注册点击事件
        * a.给标签添加 `onClick`属性,C要大写 `<button onClick={}>dd</button>`
        * b.添加当事件触发要执行的代码!
          直接在class中写要相应的方法就可以了!
          `myclick(){console.log(this)}`
        * c.修改button的onClick属性为: `<button onClick={this.myclick}>dd</button>`
        * *注意* c中时, myclick里的this指向是谁undefined,null
        * d.修改myclick方法中this的指向
        `<button onClick={  (event)=>{ this.myclick() } }>dd</button>`

- 4.要能够编辑文本框的值:
    + 上面2中的input是不无编辑!
    + 我们要通过修改this.state.hl 才能让2中input中的值变化
    + 就要给2中的input中添加`onChange事件`，在事件内容调用setState方法
    + mychange (event){
    +   //this.setState({hl:event.target.value})
    +   this.state.h1 = event.target.value // 改变数据的值
    +   this.setState({}) // 重新更新dom,内部会把h1的新值重新赋值给dom对象
    +   //this.setState({}) 是调用的render方法来更新页面的!
    + }
    `<input type="text" onChnage={ (event)=>{ this.mychange(event)} } value={this.state.hl}>`

## react中的大括号 {}

## react将数据呈现到dom

## react中注册事件

## 在react自己实现双向数据绑定

## 在react中进行dom操作

## 注意事项

## 入门难!
- 在写react时就把代码当js来用就行!

<!-- bind -->



