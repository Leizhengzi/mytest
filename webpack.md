WEBPACK：

这个小教程将通过一个简单的例子来指导你。

	你将会学到：
		. 如何安装webpack
		. 如何使用webpack
		. 如何使用loaders
		. 如何使用开发服务器
安装WEBPACK
	
	你需要安装有node.js   安装链接： https://nodejs.org/
	打开你的终端: windows 按ctrl + R，输入cmd，回车打开终端输入以下命令，linux或者mac打开系统终端即可。下面$只是代表一个标识，无意义，只输入其后面内容即可
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
	然后预编译
	$ webpack ./entry.js bundle.js
	刷新浏览器，看下刷新后的结果应该是：It works from content.js
	提示：webpack将分析你的入口文件和其它文件的依赖关系。这些文件（被叫做模块）也被包含在你bundle.js中，webpack将给每个模块一个唯一id然后保存所有模块通过id来访问在bundle.js文件。在开启的时候仅仅只有入口模块被执行。运行很短提供require函数，然后执行需要的依赖。
	
第一个LOADER

	我们想加载一个css文件到我们的应用
	webpack仅能处理本机的js。
	
	