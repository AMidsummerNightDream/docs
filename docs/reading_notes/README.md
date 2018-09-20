# React 全栈

## [Webpack](/reading_notes/react/second/)
- `ES6` - 新一代的JavaScript语言标准
- `Component`组件和模块的发展历程
- 前端开发的常用工具：
  - 包管理器（`Package Manager`, 用来下载和管理前端代码库
  - 任务流工具（`Task Runner`), 用来执行一系列开发中的任务
  - 模块打包工具（`Bundler`），用来转换和合并前端代码的模式

## ES6-- 新一代的JavaScript标准
### 语言特性
1. const, let关键字
JavaScript默认是全局性的，只存在函数级作用域。let关键字声明块级作用域
const用来定义一个常量
2. 函数
- 箭头函数
箭头函数是一种更简单的函数声明方式，语法糖，永远匿名。箭头函数的this，指向外层调用它的函数（TODO）
- 函数默认参数
```js 
function desc(name = 'Niki', age = 5) {
  return `${name}is${age} years old`
}
desc()
```
- Rest 参数
函数的最后一个参数有'...'这样的前缀，它就会变成一个参数数组
  - 和arguments的区别
    - Rest参数只是没有指定变量名的参数数组，arguments是所有参数的集合
    - arguments对象不是一个真正的数组，rest参数是一个真正的数组
3. 展开操作符
'...'展开操作符，存在多个参数，多个元素或多个变量的地方就会出现
- 用于函数调用
``` js
function test (x, y, z) {

}
let agrs = [0,1,2]
test(...args)
```
- 用于数组字面量
```js
let arr1 = [1, 2, 3]
let arr2 = [4, 5, 6]
let arr3 = [...arr1, arr2]
```
- 对象展开操作
ES7的提案
```js
let mike = { name: 'mike', age: 50 }
mike = {...mkie, sex: 'male'}
```
4. 解构赋值
语法糖
- 解构数组
``` js
let foo = ['one', 'two', 'three']
let [one, two, three] = foo
```
- 解构对象
``` js
let person = {name: 'viking', age: 20}
let {name, age} = person
```
5. Class
class语法糖， ，模仿其它语言类的声明方式
js使用原型继承

``` js
class Animal {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  shout() {
    return `My name is ${this.name}, age is 4{this.age}`;
  }
  static foo() {
    return 'Here is a static method';
  }
}

const cow = new Animal('betty', 2);
cow.shout();

Animal.foo();

class Dog extends Animal {
  constructor(name, age = 2, color = 'black') {
    super(name, age);
    this.color = color;
  }
  shout() {
    return super.shout() + `,coloe is ${this.color}`;
  }
}
```
6. 模块
- AMD（Require.js)
- CMD (CommonJS)

``` js
// hello.js
export const PI = 3.14;
export function hello() {
  console.log('Hello ES6')
}
export let person = {name: 'viking'};

// main.js
import {PI, hello, person} from './hello'
```

### 使用Babel
Babel可以提前使用语言新特性
1. 配置
Babel是通过安装插件（Plugin）或预设（preset, 就是一组设定好的插件）来编译代码
配置文件.babelrc
``` js
{
  "presets": [],
  "plugins": []
}
```

##前端组件化方案
模块（module）与组件（component）。模块是语言层面的，组件更多是业务层面的概念,可以看成一个可独立使用的功能实现（包含逻辑，样式，模板，甚至图片，字体）
### js模块化方案
1. 全局变量 + 命名空间
基于一个全局变量，各模块按照各自的命名空间挂载。模块内部通过自执行函数实现局部作用域，避免污染全局作用域
缺点
  - 依赖全局变量，污染全局作用域的同时，安全性得不到保障
  - 依赖命名空间来避免冲突，可靠性不高
  - 需要依赖手动管理并控制执行顺序，容易出错
  - 需要最终上线前手动合并所有用到的模块

2. AMD&CMD
优点
  - 仅仅需要在全局环境下定义require与define，不需要其它的全局变量
  - 通过文件路径或模块自己声明模块名定位模块
  - 模块实现中声明依赖，依赖的加载与执行均由加载器操作
  - 提供了打包工具自动分析依赖并合并
  CommonJS规范不适合浏览器环境，可以通过打包工具，CommonJS模块简洁

3. ES6模块

支持复杂的静态分析，使构建工具细粒度地移除模块实现中的无用代码成为可能
### 前端的模块化和组件化
1. 基于命名空间的多入口文件组件
  - 基于第一种模块化方案
  - 不同资源分别手动引入
2. 基于模块的多入口文件组件
  - AMD模块，为JavaScript实现
  - CSS样式文件
  - 其它资源内容
  require组件对应的模块

3. 单JavaScript入口组件
browserify, webpack等现代打包工具
4. Webpack Component
- 自定义元素 （Custom Element）
- HTML模版（HTML Template）
- Shadow DOM
- HTML 的引入 （HTML Import）

## 辅助工具
### 包管理器（Package Manager）
在计算机中自动安装， 配置，卸载和升级软件包的工具组合， mac的homebrew
bower， component， spm
1. package.json
优点
  - 以文档的形式规定了项目所依赖的包
  - 可以确定每个包所使用的版本
  - 项目的构建可重复，在多人协作中更加方便
2. 包和模块
包和模块的区别和联系。包是一个用package.json文件描述的文件或文件夹。模块的要求更为具体，指任何可以被Node.js中require方法载入的文件
  - 包由main字段package.json的文件夹
  - 包括index.js的文件夹
  - 一个单独的JAvaScript文件
所有模块都是包，但不是所有的包都是模块

### 任务流工具 （Task Runner）
压缩合并代码，验证代码格式，测试代码，监视文件是否有变化等
1. Grunt
2. Gulp

### 模块打包工具
1. browserify
2. webpack

