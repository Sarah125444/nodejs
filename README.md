# nodejs
- 1.怎么通过node解析执行文件？
  - 1.创建编写javaScript脚本文件
  - 2.打开终端，定位到脚本文件所属目录
  - 3.输入node文件名执行对应的文件
  - 注意：**文件名不要node.js**
  - 4.解析执行javascript
  - 5.读写文件
- 2.核心模块：
  Node为js提供了很多服务器级别的API，这些API绝大多数都被包装到了一个具名的核心模块中了。
  例如：
  - 文件的fs核心模块
  - http服务构建的http模块
  - path路径操作模块
  - os操作系统信息模块
    如果说到模块是一个核心模块，就要马上想到如果想要使用它，就必须先使用require方法加载才能使用

```
var fs = require('fs')
var http = require('http')
```

- 3.用户自定义模块
  - 3.1 在node中没有全局作用域，只有模块作用域
    外部访问不到内部
    内部也访问不到外部

- 可以同时开启多个服务，但一定要确保不同服务占用的端口号不一致才可以

- 4.Node中的Javascript

  - ECMASCRIPT

  - 变量
  - 方法
  - 数据类型
  - 内置对象
  - Array
  - Object
  - Data
  - Math

- 5. 模块系统

  - 在Node中没有全局作用域的概念
  - 在Node中，只能通过require方法来加载执行多个Javascript脚本文件
  - require加载只能是执行其中的代码，文件与文件之间由于是模块作用域，所以不会有污染的危险。

  - 模块完全是封闭的
  - 外部无法访问内部
  - 内部也无法访问外部

  - 模块作用域固然带来了一些好处，可以加载执行多个文件，可以完全避免变量命名冲突的危险
  - 但是在某些情况下，模块和模块是需要进行通信的
  - 在每个模块中，都提供了一个对象：`exports`
  - 该对象默认是一个空对象
  - 你要做的是把需要被外部访问使用的成员手动的挂载到`exports`接口对象中
  - 然后谁来`require`这个模块，谁就可以得到模块内部的`exports`接口对象

- 6. 核心模块

  - 核心模块是由Node提供的一个个具名的模块，他们都有自己特殊的名称标识，例如：

  - fs 文件操作模块
  - http 网络服务构建模块
  - os 操作系统信息模块
  - path 路径处理模块
  - 。。。

  - 所有核心模块在使用的时候都必须手动先使用`require`方法来加载，然后才可以使用，例如：

  - `var fs = require('fs')`

- 7.http

  - require
  - 端口号
    - ip地址定位计算机
    - 端口号定位具体的应用程序
  - Content-Type
    - 服务器最好把每次响应的数据是什么内容类型都告诉客户端，而且要正确的告诉
    - 不同的资源对应的Content-Type是不一样的，具体参照：
    - 对于文本类型的数据，最好都加上编码，目的是为了防止中文解析乱码问题

- 通过网络发送文件
  - 发送的并不是文件，本质上来讲发送的是文件的内容
  - 当浏览收到服务器响应内容之后，就会根据你的content-tyoe进行对应的解析处理
  
  --------------------------------------------------------------------
  
  
  - 服务端渲染
  + 说白了就是在服务端使用模板引擎
  + 模板引擎最早诞生于服务端，后来才发展到了前端

- 服务端渲染和客户端渲染的区别
  + 客户端渲染不利于seo搜索引擎优化
  + 服务端渲染是可以爬虫抓取到的，客户端异步渲染很难被爬虫抓取到
  + 所以你会发现真正的网站既不是纯异步也不是纯服务端渲染出来的
  + 而是两者结合来做
  + 例如京东的商品列表为了用户体验，而且也不需要SEO，所以采用的是客户端渲染
- 浏览器收到HTML相应内容之后，就要开始从上到下一次解析，当在解析过程中，如果发现
  link
  script
  img
  iframe
  video
  audio
  等带有src或者href等属性的标签的时候，浏览器会自动对这些资源发起新的请求
- 在服务端中，文件中的路径就不要去写相对路径了，因为这个时候所有的资源都是通过url标识来获取的
  我的服务器开放了/public/目录，所以这里的请求路径都写成：/public/xxx
  /在这里就是url根路径的意思。浏览器在真正发请求的时候会最终把http://127.0.0.1:3000拼上
  所以这里就不能想文件路径了，把所有的文件路径都想象成url地址
- 表单是如何提交的
 + 表单中需要提交的表单控件元素必须具有name属性
 + 表单提交分为：
  1.默认的表单提交
  2.表单异步提交

- action就是表单提交的地址，就是请求的url地址
  method请求方法：
    get:
    method:

- 对于这种请求提交的请求路径，由于其中具有用户动态填写的内容
  所以你不可能通过去判断完整的url路径来处理这个请求。
  
- 网站开发模型
  + 黑盒子
  + 写代码让它变得更智能
  + 按照你设计好的套路供用户使用
- 在Node中使用art-template模板引擎
  + 安装
  + 加载
  + template.render()
- 客户端和服务端的区别
  + 最少两次请求，发起ajax在客户端使用模板引擎渲染
  + 客户端拿到的就是服务端已经渲染好的
- 如何解析请求路径中的查询字符串
  + url.parse
- 如何在Node中实现服务器重定向
  + setHeader('location',/)
  + 301 永久重定向 浏览器会记住
    - a.com b.com
    - a 浏览器不会请求a了
    - 直接跳到b了
  + 302 临时重定向
    - a.com b.com
    - a.com 还会请求a
    - a 告诉浏览器不记忆
- Express
  + art-template 模板引擎的配置
  + body-parser解析表单POST请求体
- 技术知识一种解决问题的手段，工具而已
  + 第三方工具，不要纠结
  + 先以解决问题为主
- 详解Express中的静态服务API
  + app.use('/public',express.static('./public'))


---------------------------------------------------------------------------------
- 建立项目文件夹-blog
- 初始化npm
  ```
  npm init -y
  ```
- 初始化git仓库
  ```
  git init
  ```
- 创建一个文件.gitignore  ===>忽略文件，用来配置忽略配置项（哪些东西不需要提交到github上面）
- 创建一个新的文件夹===> public 里面都是公开的静态资源
   - public文件夹下创建文件夹 ===> css  客户端需要的样式
   - public文件夹下创建文件夹 ===> img  客户端需要的图片
   - public文件夹下创建文件夹 ===> js   客户端需要的脚本
- 新建一个文件app.js
- 安装各种第三方的包（express/mongoose/art-template/express-art-template）
    - 引入各种配置文件
        ```
          var express = require('express')
          var path = require('path')

          var app = express()

          app.use('/public/', express.static(path.join(__dirname,'./public')))
          app.use('/node_modules/', express.static(path.join(__dirname, './node_modules/')))

          app.engine('html', require('express-art-template'))



          app.get('/',function(req,res){
            res.send('hello')
          })

          app.listen(5000, function(){
            console.log('running...')
          })
        ```

- 插入的新知识：
    - path路径操作模块
      - path.basename 获取路径的一个文件名 (默认包含扩展名)
      - path.dirname  获取一个路径中的目录部分
      - path.extname  获取路径中的扩展名部分
      - path.parse  把一个路径转为对象 root根路径   
      - path.join 当需要进行路径拼接的时候，推荐使用这个方法 
          + root根路径
          + dir 目录
          + base 包含后缀名的文件名
          + ext 后缀名
          + name 不包含后缀名的文件名
      - path.isAbsolute  判断一个路径是否是绝对路径

    - Node中的其他成员
        + 在每个模块中，除了`require`，`exports`等模块相关API之外，还有两个特殊的成员
        + __dirname **动态的获取**可以用来获取当前文件模块所属目录的绝对路径 
        + __filename **动态获取**可以用来获取当前文件的绝对路径
        + `__dirname` 和 `filename`是不受node命令所属路径影响的

        + 在文件操作中，使用相对路径是不可靠的，因为在Node中文件操作的路径被设计为相对于执行node命令所处的路径（不是bug）
        + 只需要把相对路径变为绝对路径就可以解决这个问题
        + 那这里我们就可以勇士`__dirname`或者`__filename`来帮我们解决这个问题
        + 在拼接路径中，为了避免手动凭借带来的一些低级错误，所以推荐多使用：`path.join()`来辅助拼接
        + 为了尽量避免刚才所描述的问题，大家以后再文件操作中使用的相对路径都统一转换为**动态的相对路径**
        > 补充:模块中的路径标识和这里的路径没关系，不受影响（相对于文件模块）

- 在Express中配置使用express-session插件
    - 安装
    ```
    npm install express-session
    ```
    - 配置
    ```
    # 该插件会为req请求对象添加一个成员：req.session默认是一个对象
    # 这是最简单的配置方式，暂且先不用关心里面参数的含义

    app.use(session({
      secret: 'keyboard cat',   配置加密字符串，它会在原有加密基础之上和这个字符串拼接起来去加密 目的是为了增加安全性，防止客户端恶意伪造
      resave: false,
      saveUninitialized: true
    }))
    ```
    - 使用
    ```
    # 添加Session数据
    req.session.foo = 'bar'

    # 获取Session数据
    req.session.foo
    ```
    提示：默认Session数据是内存存储的，服务器一旦重启就会丢失，真正的生产环境会把Session进行持久化存储
- Express中配置使用express-session插件
    + 插件也是工具 你只需要明确你的目标就可以了
    + 我们的目标是使用session来帮我们管理一些敏感信息数据状态，例如保存登陆状态
    + 写session 
      * req.session.xxx = xx
    + 读session
      * req.session.xxx
    + 删除Session
      * req.session.xxx = null
      * 更严谨的做法是`delete`语法
      * delete req.session.xxx


- Node模块加载
   + 在Node中没有全局作用域，它是文件模块作用域
   + 模块是独立的，不能因为a加载过fs了b就不需要，正确的做法是a文件需要fs则a文件就加载fs，b文件需要fs，则b文件就加载fs

- 中间件
  + 中间件的本质是一个请求处理方法，我们把用户从请求到响应的整个过程分发到多个中间件去处理，这样做的目的是提高代码的灵活性，动态可扩展
  + 同一个请求所经过的中间件都是同一个请求对象和响应对象
- 中间件的应用
  + 万能匹配（不关心任何请求路径和请求方法）
  ```
    app.use(function(req,res,next){
      console.log('Time:',Date.now())
      next()
    })
  ```
  + 只要是以'/xxx/'开头的
  ```
    app.use('/a', function(req,res,next){
      console.log('Time:',Date.now())
      next()
    })
  ```
- 路由级别中间件
  + get
    ```
    app.get('/',function(req,res){
      res.send('hello world')
    })
    ```
  + post
    ```
    app.post('/', function(req,res){
      res.send('Got a Post request')
    })
    ```
  + put
    ```
    app.put('/user', function(req,res){
      res.send('Got a PUT request at /user')
    })
    ```
  + delete
    ```
    app.use('/user', function(req,res){
      res.send('Got a DELETE request at /user')
    })
    ```
- 错误处理中间件
    ```
     app.use(function(req,res,next){
       console.error(err.stack)
       res.status(500).send('Something broke!')
     })
    ```
- 第三方中间件
  + body-parser
  + compression
  + cookie-parser
  + morgan
  + response-time
  + serve-static
  + session
