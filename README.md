# webpack4.0工程化实践
[![License: CC BY-ND 4.0](https://img.shields.io/badge/License-CC%20BY--ND%204.0-blue.svg)](https://creativecommons.org/licenses/by-nd/4.0/legalcode)

## 简介
这是一本关于webpack工程化简介的小书。

因为工作中一直在使用 webpack，也一直以来想总结一下自己关于 webpack 的一些知识、经验。于是把一些想法慢慢整理书写下来，做成一本开源、免费、简单的入门级别的小书，提供给社区。希望能够帮助到更多webpack刚入门朋友。

由于webpack4较webpack3改动较大，而最新的webpack5.0和webpack4.0较相近，因此我们采用最新版的webpack5作为演示版本。

## 本书介绍

本书为有一点前端基础的并且是 webpack 零基础的同学而作，帮助他们掌握 webpack 并且灵活地把 webpack 应用到实际项目当中。如果你有一定的 nodejs、grunt或者gulp 基础并且希望学习 webpack，而又觉得 webpack当中有些概念比难以接受和理解，希望能够从零开始学习，那么本书很适合你。但如果你已经对前端已经非常熟悉并且用过不少的前端框架和相关的组件化技术，建议你直接看官网文档。

本书并不会文档式地包含所有知识点，只会提炼实战经验中基础的、重要的、频繁的知识进行重点讲解，让你能用最少的精力深入了解实战中最需要的 webpack 知识和套路，轻装上路。如果需要更多更全面的知识点，可以参看更多的官方文档或者其他丰富的资料。

本书初定分为四个阶段，按照先易后难，先理论再实战的顺序进行讲解，务必使得大家在学习中循序渐进，理论和实践相结合。

**第一个阶段**：简介 webpack 的基本概念和基础配置，通过这些基础配置完成简单的样式打包、js打包和资源打包。

**第二个阶段**：深入了解webpack中的进阶知识，更好的完成项目的中打包优化。

**第三个阶段**：实例搭建react开发环境、vue开发环境以及typescript开发环境。

**第四个阶段**：剖析webpack源码，理解AST抽象语法树、tapable钩子的使用，完成一个简易版本的webpack打包工具。

## 目录

**第一个阶段：基本配置**

[![License: CC BY-ND 4.0](https://img.shields.io/badge/已完成-100%25-brightgreen.svg)](https://creativecommons.org/licenses/by-nd/4.0/legalcode)

* Lesson 1 - [webpack简介](http://huziketang.com/books/react/lesson1)
* Lesson 2 - [配置文件](http://huziketang.com/books/react/lesson2)
* Lesson 3 - [entry和output](http://huziketang.com/books/react/lesson3)
* Lesson 4 - [打包模式](http://huziketang.com/books/react/lesson4)
* Lesson 5 - [webpack之模块](http://huziketang.com/books/react/lesson5)
* Lesson 6 - [webpack之plugin](http://huziketang.com/books/react/lesson6)
* Lesson 7 - [devServer搭建本地开发环境](http://huziketang.com/books/react/lesson7)
* Lesson 8 - [环境区分](http://huziketang.com/books/react/lesson8)
* Lesson 9 - [webpack中的其他配置](http://huziketang.com/books/react/lesson8)
* Lesson 10 - [打包分析](http://huziketang.com/books/react/lesson8)

**第二个阶段：打包优化**

[![License: CC BY-ND 4.0](https://img.shields.io/badge/已完成-100%25-brightgreen.svg)](https://creativecommons.org/licenses/by-nd/4.0/legalcode)

* Lesson 11 - [打包优化之体积优化](http://huziketang.com/books/react/lesson17)
* Lesson 12 - [打包优化之增强缓存命中率](http://huziketang.com/books/react/lesson18)
* Lesson 13 - [打包优化之速度优化](http://huziketang.com/books/react/lesson19)
* Lesson 14 - [打包优化之Tree-Shaking](http://huziketang.com/books/react/lesson8)
* Lesson 15 - [打包优化之splitChunks](http://huziketang.com/books/react/lesson20)
* Lesson 16 - [打包优化之代码分割](http://huziketang.com/books/react/lesson21)
* Lesson 17 - [打包优化之懒加载](http://huziketang.com/books/react/lesson22)
* Lesson 18 - [打包优化之happpack](http://huziketang.com/books/react/lesson23)
* Lesson 19 - [打包优化之DllPlugin的使用](http://huziketang.com/books/react/lesson24)
* Lesson 20 - [打包优化之externals排除第三方依赖](http://huziketang.com/books/react/lesson25)

**第三个阶段：打包实战**

- Lesson 21 - [配置多页面打包](http://huziketang.com/books/react/lesson17)
- Lesson 22 - [公共类库的打包](http://huziketang.com/books/react/lesson17)
- Lesson 23 -  [typescript的开发配置](http://huziketang.com/books/react/lesson17)
- Lesson 23 - [配置react开发环境](http://huziketang.com/books/react/lesson17)
- Lesson 24 - [配置vue开发环境](http://huziketang.com/books/react/lesson17)
- Lesson 25 - [配置angular开发环境](http://huziketang.com/books/react/lesson17)
- Lesson 26 - [配置移动端适配方案](http://huziketang.com/books/react/lesson17)

**第四个阶段：内核解析**

[![License: CC BY-ND 4.0](https://img.shields.io/badge/已完成-100%25-brightgreen.svg)](https://creativecommons.org/licenses/by-nd/4.0/legalcode)

* Lesson 27 - [tapable简介](http://huziketang.com/books/react/lesson28)
* Lesson 28 - [webpack中的钩子](http://huziketang.com/books/react/lesson29)
* Lesson 29 - [AST抽象语法树](http://huziketang.com/books/react/lesson30)
* Lesson 30 - [手写webpack之](http://huziketang.com/books/react/lesson31)
* Lesson 31 - [手写webpack之](http://huziketang.com/books/react/lesson32)
* Lesson 32 - [手写webpack之](http://huziketang.com/books/react/lesson33)
* Lesson 33 - [手写webpack之](http://huziketang.com/books/react/lesson34)
* Lesson 34 - [手写loader之](http://huziketang.com/books/react/lesson35)
* Lesson 35 - [手写loader之](http://huziketang.com/books/react/lesson36)
* Lesson 36 - [手写plugin之](http://huziketang.com/books/react/lesson37)
* Lesson 37 - [手写plugin之](http://huziketang.com/books/react/lesson38)





