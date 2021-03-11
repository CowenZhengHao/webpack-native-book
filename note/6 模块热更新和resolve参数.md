## Lesson 6 -  模块热更新和resolve参数

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