## Lesson 3 - entry和output

#### 1、入口和出口：

- **为什么需要入口：**

  通过前面的概述，我们知道webpack 是一个模块打包工具，能够从一个需要处理的 JavaScript 文件开始，构建一个依赖关系图（dependency graph），该图映射到了项目中每个模块，然后将这个依赖关系图输出到一个或者多个 bundle 中。

- **入口：**

  入口即是打包文件的入口地址，webpack的`entry`支持多种类型，包括**字符串**、**对象**、**数组**。从作用上来说，包括单文件入口和多文件入口两种。

  >**字符串：** 单入口，快速创建一个只有单个文件入口的情况，例如library的封装
  >
  >**对象：** 多页面的打包，会生成多个chunk文件
  >
  >**数组：** 会将数组中的入口文件合并之后生成一个chunk文件

- **出口：**

  当不指定`output`的时候，默认输出到`dist/main.js`，一个webpack的配置，可以包含多个`entry`，但是只能有一个`output`。`output`的常用属性是：
  
  > **`output.path`：** 输出bundle文件的存放路径；
  >
  > **`output.filename`：** 输出bundle的名称。
  >
  > **`output.publicPath`：** 指定一个在浏览器被引用的URL地址（常用于资源的CDN地址）。
  >
  > **`output.library`：** 如果我们打包的目的是生成一个供别人使用的库，那么可以使用`output.library`来指定库的名称。
  >
  > **`output.libraryTarget:`** 使用`output.library` 确定了库的名称之后，还可以使用`output.libraryTarget`指定库打包出来的规范。
  >
  > **`output.externals`：** 用于去除输出的打包文件中依赖的某些第三方js模块（例如jquery，react等等），减小打包文件的体积。
  >
  > **`output.devtool`：** `devtool`是来控制怎么显示[sourcemap](http://blog.teamtreehouse.com/introduction-source-maps)，通过 sourcemap 我们可以快速还原代码的错误位置。

#### 2、不同的哈希：

- **fullhash：**

  fullhash是整个项目的hash值，其根据每次编译内容计算得到，每次编译之后都会生成新的hash，即修改任何文件都会导致所有文件的hash发生改变；在一个项目中虽然入口不同，但是hash是相同的；hash无法实现前端静态资源在浏览器上长缓存。

- **chunkhash：**

  根据不同的入口文件进行依赖文件解析，构建对应的chunk，生成相应的hash。

- **contenthash：**

  使用 chunkhash 存在一个问题，当在一个 JS 文件中引入了 CSS 文件，编译后它们的 hash 是相同的。而且，只要 JS 文件内容发生改变，与其关联的 CSS 文件 hash 也会改变，针对这种情况，可以把 CSS 从 JS 中使用[mini-css-extract-plugin](https://github.com/webpack-contrib/mini-css-extract-plugin) 或 [extract-text-webpack-plugin](https://github.com/webpack-contrib/extract-text-webpack-plugin)抽离出来并使用 contenthash。

