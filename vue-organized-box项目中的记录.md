# vue-organized-box项目中的记录

## 1、更新vue-cli4注意点

1、baseUrl报错

```
ERROR Invalid options in vue.config.js: “baseUrl“ is not allowed
```

在vue-cli3.3版本后baseUrl被废除了，字段改为了publicPath

2、配置热更新

首先安装webpack-dev-server

```
npm install --save-dev webpack-dev-server
```

配置热更新在vue.config.js中

```
devServer: {
    disableHostCheck: true
  }
```

之后在package.json中加入

```
"dev": "vue-cli-service serve && webpack-dev-server --open"
```

## 2、iconfont中彩色图标的使用

首先，彩色图标需要使用svg方式引入

在main中引入iconfont.js

在组件中使用：

```vue
<svg class="icon" aria-hidden="true">
    <use :xlink:href="`#icon--box${Math.floor(Math.random() * 5 + 1)}`"></use>
</svg>
```

css：

```scss
.icon {
    margin-top: 20px;
    width: 110px;
    height: 110px;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
}
```

**注意点：**

因为我一开始在iconfont项目库中改了symbol的class

![image-20211227222629514](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211227222629514.png)

便以为在vue组件中使用的href指向的是icon-box，结果发现在iconfont下载下来的iconfont.html中其实是以#开头的。所以加上#就对了。