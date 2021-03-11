## Lesson 5 - loader的使用

#### 1、loader简介：

- **loader简介：**

  在webpack中，不同的模块需要使用不同类型的模块处理器来处理，不同的文件类型对应不同的打包loader，比如处理js的babel-loader、处理css文件的css-loader等。

- **loader配置：**

  loader是定义在module项中的，基本的配置有两个：

  - **module.noParse：**

    `module.noParse`配置项可以让Webpack 忽略对部分没采用模块化的文件的递归解析和处理，这样做的好处是能提高构建性能。

  - **module.rules：**

    `odule.rules`是在处理模块时，将符合规则条件的模块，提交给对应的处理器来处理，通常用来配置 loader，其类型是一个数组，数组里每一项都描述了如何去处理部分文件。

  ```shell
  const path = require('path');
  module.exports={
      mode:'production',
      entry:'./src/js/index.js',
      output:{
          path:path.resolve(__dirname,'dist')
      },
      module:{
          noParse:/jquery|lodash/,
          rules:[
              {
                  test:/\.js$/,
                  include:path.resolve(__dirname,'src'),
                  loader:'babel-loader'
              }
          ]
      }
  }
  ```

#### 2、loader的执行：

- **执行顺序：**

  webpack中的loader执行顺序是从右向左，或者从后向前。如果需要调整loader的执行顺序，可以使用`enforce`，取值为`pre|post`，`pre`表示放在最前面，`post`放到最后面。

- **loader配置：**

  loader的配置一般是配置在option参数中，option参数是一个对象，在对象中配置不同的属性。

#### 3、Babel的使用：

- **Babel是什么：**

  Babel 是 JavaScript 的编译器，通过 Babel 可以将我们写的最新 ES 语法的代码轻松转换成任意版本的 JavaScript 语法。随着浏览器逐步支持 ES 标准，我们不需要改变代码，只需要修改 Babel 配置即可以适配新的浏览器。

- **配置：**

  babel的配置文件主要有两种：

  > **package.json配置：** 在package.json文件中配置`babel`属性。
  >
  > **.babelrc文件/.babelrc.js文件：** babel会在正在被转义的文件当前目录查找.babelrc文件。

- **插件系统：**

  Babel 的语法转换是通过强大的插件系统来支持的。Babel 的插件分为两类：转换插件和语法解析插件。常见的插件如下：

  > **@babel/preset-env：**官方推出的插件预设，它可以根据开发者的配置按需加载对应的插件。
  >
  > **@babel/polyfill：** babel只负责进行语法转换，但是在ES5中，有些对象、方法是不支持的，就必须使用`@babel/polyfill`来做模拟处理。
  >
  > **@babel/runtime：** @babel/polyfill直接修改内置的原型，造成全局污染，并且无法按需引入。

- **@babel/polyfill的按需加载：**
  
  前面介绍了`@babel/polyfill`和`@babel/runtime`两种方式来实现浏览器 polyfill，两种方式都比较繁琐，而且不够智能，我们可以使用`@babel/preset-env`的`useBuildIn`选项做 polyfill，这种方式简单而且智能。
  
  ```shell
  {
      "presets": [
          [
              "@babel/preset-env",
              {
                  "useBuiltIns": "usage",
                  "corejs": 3
              }
          ]
      ]
  }
  ```
  
  > 配置了**"useBuiltIns": "usage"** 之后，在使用polyfill的时候就不需要单独引入了，打包时会自动分析并引入所需代码，同时要指定`corejs`的版本。

- **Babel原理：**

  Babel 是一个 JavaScript 的静态分析编译器，所谓静态分析指的是在不需要执行代码的前提下对代码进行分析和处理的过程（执行时进行代码分析叫动态分析）。

  要实现 Babel 从一个语法转换成另外一个语法，需要经过三个主要步骤：解析（Parse），转换（Transform），生成（Generate）。

  **解析：**指的是首先将代码经过词法解析和语法解析，最终生成一颗 AST（抽象语法树），在 Babel 中，语法解析器是[`Babylon`](https://github.com/babel/babylon)；

  **转换：**得到 AST 之后，可以对其进行遍历，在此过程中对节点进行添加、更新及移除等操作，Babel 中 AST 遍历工具是[`@babel/traverse`](https://github.com/babel/babel/tree/master/packages/babel-traverse)

  **生成：**经过一系列转换之后得到的一颗新树，要将树转换成代码，就是生成的过程，Babel 用到的是[`@babel/generator`](https://github.com/babel/babel/tree/master/packages/babel-generator)

#### 

