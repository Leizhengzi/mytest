Phpstorm 快捷开发－－用法指南（主要针对mac系统，windows系统需要将command键换成ctrl键）

常用快捷键：
		
		command + D  复制当前行或复制选中的内容
		command + 删除键  删除当前行或选中的内容所包含的行
		command + R   查找替换
		command + G   选中单词
		command + C   选中一行
		alt + shift + 上下箭头  上下行互换
		command + shift + 上下箭头  上下函数互换
		command + shift + v 显示最近粘贴内容
		command + b  跳到声明处
		command + o 类名查找
		command + p 文件查找
		shift + shift  各种搜索（包括文件名,函数,类,etc.）
		alt + shift + c  快速回顾最近修改的项目
		ctrl + alt + t  插入环绕代码
		ctrl + alt + f12  跳转至当前文件所在磁盘位置
		alt + 左右键  移动一个单词字符长度
		command + 左右键  移动行头行尾
		ctrl + a 移动到行头
		ctrl + e 移动到行尾
		alt + up 以标签的方式显示文件位置
		alter + 鼠标左键  多点编辑
		command + shift + enter 向下插入一行
		command ＋ 大写切换 ＋ enter 向上插入一行
		command + n 快速为每个成员属性生成getter,setter方法
		ctrl + i 快速生成插入魔术方法
		ctrl + o 复写父类方法
		
编辑器默认快捷键：

		command + j  插入活跃代码提示 
		command ＋ ／  注释当前行代码
		command + shift + /  多行注释
		command + shift + u 字母大小写转换
		command + f 查找
		command ＋ L  跳转到指定行
		command + alt + L 格式话代码（要先定义好规则，下面讲）
		command + z 撤销
		command ＋ shift + z 反撤销	
		command ＋ x 剪切行
		command + '-/+' 折叠项目中的任何代码块
		command ＋ shift ＋ r 快速查找关键字在整个项目位置，可替换
	
		
一些比较好用的插件：
远程连接服务器：
	
		1.选择tools(工具)－>deployment(部署)－>browse remote host(配置远程连接主机)
		2.然后弹出个弹窗，输出项目名称，确定，在右侧边栏在项目名称旁边有...的图框，点击开始配置远程的一些设置！！
		3.然后选择对应的协议，设置好主机，端口，点击右边的test connection 来测试是否成功配好！
		4.确认成功后就配置项目的路径，访问账号和密码都配好后点击上方的标签栏mapping,将本地对应的项目路径（默认即可）和服务器上的路径对应好，点击确定即可！然后你就可以在本地开发，可自动也可手动同步远程服务器项目了。自动只需选上第1步部署下面的automatic upload 即可。
		
database工具：

		1. 选择view(视图)－>tool windows ->database
		2. 在右侧栏会出现一个关于database配置的内容，点击＋号，选择database source ->对应的数据库，这里以mysql为例
		3. 选择mysql后，就出来一个弹窗，同样是配置路径，主机，账号，密码，具体跟远程连接的方式一样，配好后就会出现数据库的内容了，库和表，而去也是可以设置时时同步。
		
前端emmet插件：

		这个插件是编辑器自带的，在写html的时候这些共性内容，比如： div.test#mytest ->tab 就会变成
		<div class="test" id="mytest"></div>
    又如： table>thead>(th.test)*4 ->tab =>
    	<table>
    		<thead>
    			<th class="test"></th>
    			<th class="test"></th>
    			<th class="test"></th>
    			<th class="test"></th>
    		</thead>
    	</table>
		熟悉这些快捷用法，一定给你的编程带来事半功倍效果

页面无刷新样式时时同步liveedit插件：

		1.键入command + ／file->setting default, 打开编辑器配置	
		2.在搜索框内输入plugin->点击下面browse responsitories 按钮－>左上角输入liveedit
		3. 在右框中点击安装，按照提示一步一步完成。
		如果有火狐浏览器，搜索css-x-fire有同样的功能。
		
一个高效开发的插件live template:

		command + shift + a ->输入live template 配置自己的模版吧！ 
	
		
			

