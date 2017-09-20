# 框架心得

## express
-	Express是目前最流行的基于Node.js的Web开发框架，可以快速地搭建一个完整功能的网站。

### 结构目录
 + 这是我的结构 ：

![](https://i.imgur.com/0TKbr0L.png)

	-	根目录为static.
	-	根目录下的public文件夹，是静态文件（如img文件，css文件，js文件）根目录。
	-	根目录下的view是模板文件的根目录。
	-	根目录中的app.js是启动文件。
	-	根目录里的data.json是要用到的数据。

### 基本步骤
-	启动文件部分
![](https://i.imgur.com/hMtUBFv.png)

![](https://i.imgur.com/NzXAcVw.png)

![](https://i.imgur.com/ZO8qbWi.png)

-	首页部分
![](https://i.imgur.com/OPowY9i.png)

- 	实际效果
![](https://i.imgur.com/rFqaeYZ.png)

### Tips
+	托管静态资源文件,当某个请求的url是以/static开头的，那么就把该文件定向到static目录
+	express.static是express 4.0中唯一的内置中间件，不需要额外引入
+ 	模板的诞生是为了将显示与数据分离，模板技术多种多样，但其本质是将模板文件和数据通过模板引擎生成最终的HTML代码。
+	模板引擎就是利用正则表达式识别模板标识，并利用数据替换其中的标识符。
![](https://i.imgur.com/9yayy9F.png)
+ swig是JS模板引擎，它有如下特点：
	-	支持大多数主流浏览器。
	-	表达式兼容性好。
	-	面向对象的模板继承。
	-	将过滤器和转换应用到模板中的输出。
	-	可根据路劲渲染页面。
	-	支持页面复用。
	-	支持动态页面。
	-	可扩展、可定制。

