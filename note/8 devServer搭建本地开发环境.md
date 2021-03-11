## Lesson 8 -  devServer搭建本地开发环境

#### 1、简介：

- **devServer：**

  [webpack-dev-server](https://github.com/webpack/webpack-dev-server)是一个基于 [Express](https://expressjs.com/) 的本地开发服务器。它使用 [webpack-dev-middleware](https://github.com/webpack/webpack-dev-middleware) 中间件来为通过 Webpack 打包生成的资源文件提供 Web 服务。

  它还有一个通过 Socket IO 连接着 webpack-dev-server 服务器的小型运行时程序。webpack-dev-server 发送关于编译状态的消息到客户端，客户端根据消息作出响应。

- **inline模式和iframe模式：**

  在开发中，我们希望边写代码，边看到代码的执行情况，webpack-dev-server 提供自动刷新页面的功能可以满足我们的需求。webpack-dev-server 支持两种模式的自动刷新页面。

  > **iframe 模式：**页面被放到一个 iframe 内，当发生变化时，会重新加载；
  >
  > **inline 模式：**将 webpack-dev-server 的重载代码添加到产出的 bundle 中。

- **配置devServer：**

  webpack-dev-server 被 Webpack 作为内置插件对外提供了，这样可以直接在对应的 Webpack 配置文件中通过`devServer`这个属性的配置来配置自己的`webpack-dev-server`。

  > **port：** 表示服务器的监听端口；
  >
  > **contentBase：** 表示服务器将从哪个目录去查找内容文件（即页面文件，比如 HTML）；
  >
  > **open：** 自动打开默认浏览器。
  >
  > **hot：** 开启模块热更新。

  ```shell
  devServer: {
      contentBase: path.join(__dirname, 'build'),
      port: 9000,
      open: true,
      hot: true
  }
  ```

- **HRM（模块热更新）：**

  HMR 即模块热替换（Hot Module Replacement）的简称，它可以在应用运行的时候，**不需要刷新页面**，就可以直接替换、增删模块。

  开启HRM需要以下三个步骤：

  - 设置`devServer.hot=true`，`devServer.inline=true`（默认）；

  - 添加 plugins：`new webpack.HotModuleReplacementPlugin()`；

  - 修改入口文件添加 HMR 支持代码：

    ```javascript
    if (module.hot) {
        // 通知 webpack 该模块接受 hmr
        module.hot.accept(err => {
            if (err) {
                console.error('Cannot apply HMR update.', err);
            }
        });
    }
    ```

#### 2、高级使用：

- **proxy：**

  在实际开发中，本地开发服务器是不能直接请求线上数据接口的，这是因为浏览器的同源安全策略导致的跨域问题，我们可以使用`devServer.proxy`来解决本地开发跨域的问题。

  ```javascript
  module.exports = {
      //...
      devServer: {
          proxy: {
              '/api': 'http://baidu.com'
          }
      }
  };
  ```

  那么，我们请求`/api/users`则会被转发到`http://baidu.com/api/users`线上地址。

- **自定义中间件：**

  在 webpack-dev-server 中有两个时机可以插入自己实现的中间件，分别是在`devServer.before`和`devServer.after`两个时机，即 webpack-dev-server 加载所有内部中间件之前和之后两个时机。
  
  ```javascript
  devServer: {
          contentBase: path.join(__dirname, 'build'),
          port: 9000,
          open: true,
          hot: true,
          proxy:{
              '/api':'http://baidu.com'
          },
          before(app,server){
              app.get('/test',(req,res)=>{
                  res.send({status:"200",data:{name:"cowen",age:32}})
              })
          }
      }
  ```
  
  