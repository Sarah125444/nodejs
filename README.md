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

