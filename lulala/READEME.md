2017-07-06  本次有如下更新

	#1接口{bind_sensor.php}新增【nick】参数，支持对设备设置昵称了
	#2接口{unbind_sensor.php}更改【imei】为数组类型，支持批量解绑了
	#3新增接口: 
	         {change_nick.php}      <==> 更改设备昵称
	         {show_sensor.php}      <==> 显示设备列表 
	         {enable_alarm.php}     <==> 用报警设置
	         {disable_alarm.php}    <==> 关闭报警
	         {show_alarm_log.php}   <==> 显示报警列表
	         {remove_alarm_log.php} <==> 删除某个报警记录
	
2017-07-10 本次更新

	#1接口{trace.php}请求返回信息更改
	#2新增接口:
	         {trace_my.php}   <==> 显示所有设备的坐标信息和围栏信息