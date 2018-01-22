# fez-demo-cdn
fez-demo-cdn 是为项目静态资源添加CDN地址的示例。

## 使用示例
#### 首先将fez-demo-cdn

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

- 执行 `gulp dist` 做项目上线发版
- 项目中所有的静态资源链接Url都会被添加上CDN地址前缀，比如：

```
//index.html

<!DOCTYPE HTML><html lang="zh-CN"><head><meta charset="UTF-8"><meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"><meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no"><meta name="renderer" content="webkit"><meta name="apple-mobile-web-app-capable" content="no"><meta name="format-detection" content="telephone=no"><title>添加CDN地址Demo</title><meta name="keywords" content=""><meta name="description" content=""><link rel="stylesheet" href="//static.fezcdn.com/cdndemo/static/css/index-dc24eb5359.css"></head><body><div class="content"><h3>《香港之行》</h3><p>雨后登高望山楼<br>溢彩香江曜中秋<br>悠游凌霄美食汇<br>不负此行挂心头</p></div><script src="//static.fezcdn.com/cdndemo/static/js/index-f3d06ba2f6.js"></script></body></html>
```

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

#### 验证效果

- 发布项目

```
gulp dist
```

- 启动上线代码测试环境

```bash
gulp test
```