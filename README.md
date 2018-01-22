# fez-demo-cdn

为项目静态资源添加CDN地址示例。

## 使用示例
#### 首先将fez-demo-cdn 项目下载到FEZ工程目录

```bash
git clone git@github.com:furic-zhao/fez-demo-cdn.git
```

#### 使用FEZ开发框架在网页中添加静态资源CDN地址

- 在项目`fez.config.js`的`useCdn`中设置`available`为`true`，并在`base`字段填写CDN地址，比如：

```
//fez.config.js 文件

export default {
  useCdn: {
    available: true,
    base: "//static.fezcdn.com/cdndemo/"
  }
}
```

- 执行 `gulp dist` 上线发版
- 项目中所有的静态资源链接Url都会被添加上CDN地址前缀，比如：

```
//index.html

<!DOCTYPE HTML>
<html lang="zh-CN">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no">
  <meta name="renderer" content="webkit">
  <meta name="apple-mobile-web-app-capable" content="no">
  <meta name="format-detection" content="telephone=no">
  <title>添加CDN地址Demo</title>
  <meta name="keywords" content="">
  <meta name="description" content="">
  <link rel="stylesheet" href="//static.fezcdn.com/cdndemo/static/css/index-dc24eb5359.css">
</head>

<body>
  <div class="content">
    <h3>《香港之行》</h3>
    <p>雨后登高望山楼
      <br>溢彩香江曜中秋
      <br>悠游凌霄美食汇
      <br>不负此行挂心头</p>
  </div>
  <script src="//static.fezcdn.com/cdndemo/static/js/index-f3d06ba2f6.js"></script>
</body>

</html>

```

> FEZ自动默认使用相对路径引用静态资源，即：`<script src="static/js/demo.js">`

```
//index.dc24eb5359.css

@font-face {
  font-family: SentyTang;
  src: url(//static.fezcdn.com/cdndemo/static/fonts/SentyTang-82f052814d.eot);
  src: url(//static.fezcdn.com/cdndemo/static/fonts/SentyTang-82f052814d.eot?#iefix) format("embedded-opentype"), url(//static.fezcdn.com/cdndemo/static/fonts/SentyTang-50024d3abd.woff) format("woff"), url(//static.fezcdn.com/cdndemo/static/fonts/SentyTang-69460e4af2.ttf) format("truetype"), url(//static.fezcdn.com/cdndemo/static/fonts/SentyTang-35a8902ac9.svg#SentyTang) format("svg");
  font-style: normal;
  font-weight: 400
}

body {
  background-image: url(//static.fezcdn.com/cdndemo/static/images/bg-47c6460303.jpg);
  -moz-background-size: 100%;
  background-size: 100%
}
```

> 样式中请尽量使用相对路径来引入图片和字体文件，即:`background-image:url('../images/bg.jpg')`，FEZ会自动做路径转换。

#### 验证效果

- 发布项目

```
gulp dist
```

- 启动上线代码测试环境

```bash
gulp test
```

#### 分类配置地址(高级配置)

```
//fez.config.js 文件

export default {
  useCdn: {
    available: false,
    extFile: 'css,html', //可以替换CDN地址的文件扩展名
    base: "//fezcdn.com/cdndemo/" //默认CDN地址
    js: "http://js.fezcdn.com/cdndemo/", //脚本CDN地址
    css: "http://css.fezcdn.com/cdndemo/", //样式CDN地址
    images: "http://img.fezcdn.com/cdndemo/", //图片CDN地址
    fonts: "http://fonts.fezcdn.com/cdndemo/" //字体CDN地址
  }
}
```

> 如果js、css、images、fonts未配置，FEZ默认调用base中的配置。在`extFile`中可配置要处理的文件扩展名，FEZ默认只对`css`和`html`中引用的Url地址添加CDN前缀。