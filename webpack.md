WEBPACK：

这个小教程将通过一个简单的例子来指导你。

	你将会学到：
		. 如何安装webpack
		. 如何使用webpack
		. 如何使用loaders
		. 如何使用开发服务器
安装WEBPACK

	你需要安装有node.js   安装链接： https://nodejs.org/
	打开你的终端: windows 按win + R，输入cmd，回车打开终端输入以下命令，linux或者mac打开系统终端即可。下面$只是代表一个标识，无意义，只输入其后面内容即可
	$ npm install webpack -g
	提示：这个命令让webpack命令可以使用

设置编译

	首先创建一个空目录，然后进入目录。
	创建这些文件：
	   entry.js
		添加内容：
			document.write("It works.");
		index.html
		添加内容：
			<html>
			    <head>
			        <meta charset="utf-8">
			    </head>
			    <body>
			        <script type="text/javascript" src="bundle.js" charset="utf-8"></script>
			    </body>
			</html>
		保存退出！
	运行以下命令：
	$ webpack ./entry.js bundle.js
	它将编译你的文件然后创建一个bundle文件
	如果成功将会显示这些信息：
	Version: webpack 1.12.11
	Time: 51ms
	    Asset     Size  Chunks             Chunk Names
	bundle.js  1.42 kB       0  [emitted]  main
	chunk    {0} bundle.js (main) 28 bytes [rendered]
	    [0] ./tutorials/getting-started/setup-compilation/entry.js 28 bytes {0} [built]
	在浏览器中打开index.html。它应该显示it works.

第二个文件

	接下来我们将移动一些代码到其他文件
	创建文件：
		content.js
		添加内容：
		module.exports = "it works from content.js";
	修改文件：
		entry.js
		修改内容：
		去掉 document.write("It works.");
		添加 document.write(require("./content.js"));
	然后重新编译
	$ webpack ./entry.js bundle.js
	刷新浏览器，看下刷新后的结果应该是：It works from content.js
	提示：webpack将分析你的入口文件和其它文件的依赖关系。这些文件（被叫做模块）也被包含在你bundle.js中，webpack将给每个模块一个唯一id然后保存所有模块通过id来访问在bundle.js文件。在开启的时候仅仅只有入口模块被执行。运行很短提供require函数，然后执行需要的依赖。

第一个LOADER

	我们想加载一个css文件到我们的应用
	webpack仅能处理本机的js,所以我们需要css-loader去处理css文件。我们也需要style-loader去应用css文件上的样式。
	运行命令：
	$ npm install css-loader style-loader 来安装loader.
	注意：它们需要被安装在本地，不需要用 -g 这个参数
	这个将为你创建一个node_modules文件夹，里面包含loaders.
	让我们来使用它们：
	创建文件：
		style.css
		添加内容：
		body {
		    background: yellow;
		}
	修改文件：
		entry.js
		修改内容：
		添加    require("!style!css!./style.css");
  			   document.write(require("./content.js"));
	重新编译一下
	$ webpack ./entry.js bundle.js
	然后去浏览器查看下效果
	提示：通过前缀加载一个模块请求，这个模块就会通过一个loader管道。这些loaders用一个特殊的方式传输文件内容。这些传输被应用后，结果会变成一个js模块。

绑定 LOADERS

	我们不想写太长的require: require("!style!css!./style.css");
	我们能绑定文件扩展去加载，所以我们只需要写：require("./style.css");
	修改文件：
		entry.js
		去掉：require("!style!css!./style.css");
		添加：require("./style.css");
			 document.write(require("./content.js"));
    运行命令编译文件：
   	$ webpack ./entry.js bundle.js --module-bind 'css=style!css'
   	提示：一些环节可能需要双引号：--module-bind "css=style!css"
   	刷新浏览器，应该得到一样的结果

 一个配置文件

 	我们想将配置参数移入到一个文件中
 	添加文件:
 		webpack.config.js
 	添加内容：
 		module.exports = {
		    entry: "./entry.js",
		    output: {
		        path: __dirname,
		        filename: "bundle.js"
		    },
		    module: {
		        loaders: [
		            { test: /\.css$/, loader: "style!css" }
		        ]
		    }
		};
	然后我们可以运行：
	$ webpack
	然后去编译
	提示：这个webpack命令行将试着在当前目录去加载webpack.config.js文件。

一个漂亮的输出

	如果项目增加编译可能需要更长的时间。所以我们想显示某种进步，如我们想要颜色...
	我们能获得用下面这个命令
	$ webpack --progress --colors

监控模式

	我们不想手动去编译在每一次的改变之后...
	执行命令：
	$ webpack --progress --colors --watch
	webpack能缓存未改变的模块在编译的时候输出文件
	提示：当我们使用监控模式，webpack将在所有文件安装watchers,将被用来编译处理。如果被检测到有改变，他将再次运行编译。当缓存被启用的时候，webpack将保持每个模块在缓存中，然后将重复使用它，如果它未改变。

开发服务器

	开发服务区甚至更好。
	执行命令：
	$ npm install webpack-dev-server -g
	webpack-dev-server --progress --colors
	这个将绑定本地小的专用服务器localhost:8080，服务于你静态资源也有bundle(自动编译)。他自动更新浏览器当一个bundle被重新编译的时候。在你浏览器打开
	http://localhost:8080/webpack-dev-server/bundle。
	提示：开发服务器使用webpack的监控模式。它还可以防止webpack发出产生的文件到磁盘上。代替它保存这些文件在缓存中。

# test


