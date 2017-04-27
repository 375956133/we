### 创建一个服务
## express 就是基于node.JS平台的web应用开发框架
* var express=require("express")
* var  app=express()
* // 它就是个路由
* app.get("/",function(req,res){
	res.send("hello world")
})

* app.get("/a",function(req,res){
	res.send("hello express")
})
* app.listen(3000,function(){
	console.log("running...")
})

