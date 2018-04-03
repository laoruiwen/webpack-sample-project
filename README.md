####写在前面的话
>相信要入门Webpack的小伙伴第一个就能搜到这篇文章[《入门Webpack，看这篇就够了》](https://www.jianshu.com/p/42e11515c10f),不过作者的版本是3.5.3，目前下的最新的4.3.0，按照作者写的，像我这种刚入门的小白会碰到很多坑呀。这里会使用webpack@4按照[zhangwang](https://www.jianshu.com/u/7091a52ac9e5)的思路再走一遍。

>此文涉及的知识点比较多，适合新手看，请各位老鸟选择性略过，谢谢！

####安装
- 安装[node.js](https://nodejs.org/en/download/)

- 全局安装`webpack`

```
//全局安装
cnpm install -g webpack
```
>作者使用的都是`npm`，这里推荐使用`cnpm`，安装速度较快。
>- `npm`：node.js的包管理器，用于node插件管理（包括安装、卸载、管理依赖等）
>- `cnpm`：淘宝npm在国内的镜像，同步频率目前为 10分钟

- 全局安装`webpack-cli`
```
cnpm install -g webpack-cli
```
>webpack@4将命令行相关的内容都迁移到 `webpack-cli`

- 新建工程，命名webpack sample project。
>不知道大家用的是什么IDE，我用的是IDEA，还是挺好用的，有自带的Terminal。

- 创建package.json文件
```
cnpm init
```
>- 定义这个项目所需要的各种模块，以及项目的配置信息（比如名称、版本、许可证等元数据）
>- 测试项目，一直回车就好

- 在此项目根目录下安装`webpack`
```
//安装到你的项目目录
cnpm install --save-dev webpack
```

- 在此项目根目录下安装`webpack-cli`
```
//安装到你的项目目录
cnpm install --save-dev webpack-cli
```

>- `-save || -S      // 运行依赖（发布）`
>- `-save-dev || -D     //开发依赖（辅助）`

####写入测试文件
- 工程目录如下：
![menu.png](https://upload-images.jianshu.io/upload_images/11133151-a2efb4b631e481c5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- index.html
```
<!-- 引入打包后的main.js文件 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>Webpack Sample Project</title>
</head>
<body>
<div id='root'>
</div>
<script src="../dist/main.js"></script>
</body>
</html>
```

>不同点：
webpack@4不需要定义输出文件
它会将./dist/main.js作为默认值

- Greeter.js
```
<!-- 定义一个返回包含问候信息的html元素的函数,
并依据CommonJS规范导出这个函数为一个模块 -->
module.exports = function() {
    var greet = document.createElement('div');
    greet.textContent = "Hi there and greetings!";
    return greet;
};
```

- index.js
```
<!-- 把Greeter模块返回的节点插入页面 -->
const greeter = require('./Greeter.js');
document.querySelector("#root").appendChild(greeter());
```

>不同点：
webpack@4不需要定义入口点
它会将./src/index.js作为默认值

####运行webpack
- 此时直接在Terminal中输入webpack
```
webpack
```

- 会自动生成dist文件夹和dist下的main.js

![webpack.png](https://upload-images.jianshu.io/upload_images/11133151-15328883e78b73ab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 用浏览器打开index.html

![result.png](https://upload-images.jianshu.io/upload_images/11133151-b49fd7544d9416ae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 完成（有没有很开心呢，反正我是小小的开心了一下）

>`webpack {entry file} {destination for bundled file} `这种形式webpack@4已不支持

>具体代码请参照https://github.com/laoruiwen/webpack-sample-project
