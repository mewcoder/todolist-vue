# vue练手小项目todolist

> 一个简单的vue练手项目，主要练习vue组件化和组件之间的值传递

## 1. 效果图

![效果图](https://i.loli.net/2020/09/09/YMJCqDAG8etxBTs.png)


## 2. 说明


### 1. 使用Vue脚手架vue-cli搭建项目

安装：

```
npm install -g vue-cli
```

使用：

```
vue init webpack 
```

### 2. 使用stylus 

安装：

```
npm install -D stylus stylus-loader
```


### 3. 下载运行
1. 安装依赖
```
npm install 
```
2. 运行
```
npm dev
```
3. 打包
```
npm build
```

## 3.静态文件部署

### 1.静态预览
脚手架执行`npm run build`生成的静态文件，本地访问会显示空白，资源无法加载。

需要修改两个配置：

1.index.js

 `assetsPublicPath: '/'`修改为` assetsPublicPath: './',`

2.utils.js
```js
   if (options.extract) {
      return ExtractTextPlugin.extract({
        use: loaders,
        fallback: 'vue-style-loader',
        publicPath: '../../'  //新增这一行
      })
    } e
```

### 2.部署到GitHub Pages

1.安装gh-pages
```
sudo npm install gh-pages --save-dev
```

2.修改package.json

```
      "predeploy": "npm run build",
      "deploy": "gh-pages -d dist"
```

3.执行
```
npm run deploy
```


> 参考来源
> 1. http://blog.brojie.cn/web/todolist
> 2. https://github.com/Elgar17/vue_Todo