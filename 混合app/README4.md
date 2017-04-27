# app

## webpack
- 不仅仅是把js合并在一起，还有css
- 如果项目使用到了图片!


> webpack 本身只能合并js
> 要合并css到js中需要: style-loader css-loader
> 需要一个叫作file-loader
    + 作用是把css中的图片复制到dist目录，会自动处理好
    图片的引用路径!
## webpack 压缩js
## webpack 复制html到dist目录!

## 码云
- https://git.oschina.net/
- [博学谷项目地址](http://git.oschina.net/huoqishi/react-bxg) 

## 关于接口文档中请求数据的格式问题
- 通常给后端发参数有两种格式:
    + A.  `a=1&b=2`
        * jquery发ajax请求，发送的这种格式的数据
        * 对应的请求头: 
            `content-type: application/x-www-form-urlencoded`

    + B.  `{"a":1,"b":2}`  json格式的字符串
        * angular, axios
        * 对应的请求头: 
            `content-type: application/json`

- 后端是根据请求头: content-type去判断前端发送的数据是什么格式
    + 而不是判断数据本身 

## react版博学谷


## 下午说下sass问题
- less
- 当我们用npm 下载包是，是从npm官网下载
- nrm 用来选择我们npm下载包是，会从哪个服务器下载
- `npm install -g nrm`
- `nrm ls`
- `nrm use taobao` // 把下载地址改变为淘宝

## yarn 是和npm 一样的包管理工具
- yarn 和npm 是可以混用
- 是因为yarn 和npm 都会把包下载 `node_modules`目录
- 安装: `npm install -g yarn`
- 下载一个包: `yarn add webpack --save-dev`

## bower
- 前端专用的包管理工具
- 安装: `npm install -g bower`
- 下载包: `bower install jquery`

## react-native
- weex

## 注意
class 改为 className
for 改为 htmlFor