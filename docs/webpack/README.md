# Webpack

## Entry
## Output

## Mode

``` js
module.exports = {
  mode: 'production'
};
```
``` bash
$ webpack --mode=production
```

``` js
module.exports = {
+ mode: 'development'
- devtool: 'eval',
- plugins: [
-   new webpack.NamedModulesPlugin(),
-   new webpack.NamedChunksPlugin(),
-   new webpack.DefinePlugin({ "process.env.NODE_ENV": JSON.stringify("development") }),
- ]
}
```

```js
module.exports = {
+  mode: 'production',
-  plugins: [
-    new UglifyJsPlugin(/* ... */),
-    new webpack.DefinePlugin({ "process.env.NODE_ENV": JSON.stringify("production") }),
-    new webpack.optimize.ModuleConcatenationPlugin(),
-    new webpack.NoEmitOnErrorsPlugin()
-  ]
}
```

## Plugins

### html-webpack-plugin

``` js
new htmlWebpackPlugin({
	title: '标题', //生成html文件的标题
    filename: 'index.html', //生成html文件的文件名，默认是index.html
    template: 'index.html', // 指定生成的文件依赖的html文件模板，模板类型可以是html、jade、ejs等
    inject: 'head'， // 四个值： true body head false
    favicon: 'path/to/my_favicon.ico', //生成的html文件生成一个 favicon ,值是一个路径
    minify: {
      removeAttributeQuotes: true // 移除属性的引号
    },
    chunks: ['index','main'], //用于多入口文件，当你有多个入口文件，那就回编译后生成多个打包后的文件，那么chunks 就能选择你要使用那些js文件
    excludeChunks: ['main'] //排除某些chunk
})
```
inject
- `true` 默认值，script标签位于html文件的 body 底部
- `body` script标签位于html文件的 body 底部
- `head` script标签位于html文件的 head中
- `false` 不插入生成的js文件，这个几乎不会用到的

### webpack-dev-server

只有在开发环境下配置才有用

``` js
module.exports = {
  //...
  devServer: {
    port: 8080
  }
};
```
