平滑重启nginx
		
		kill -HUP 主进程号货进程号文件路径
		或者使用
		／usr/nginx/sbin/nginx -s reload
		
注意：修改了配置文件后最好检查一下修改过的配置文件是否正确，以免重启后nginx出现错误影响服务器稳定运行。

判断nginx配置是否正确命令如下：

		nginx -t -c /usr/nginx/conf/nginx.conf
		或者
		/usr/nginx/sbin/nginx -t
		
nginx重启

		/usr/local/nginx/sbin/nginx -s reload
		
用root权限重启

		killall nginx
		

      