2017-07-06  本次更新内容：

	#1接口{bind_sensor.php}新增【nick】参数，支持对设备设置昵称了
	#2接口{unbind_sensor.php}更改【imei】为数组类型，支持批量解绑了
	#3新增接口: 
	         {change_nick.php}      <==> 更改设备昵称
	         {show_sensor.php}      <==> 显示设备列表 
	         {enable_alarm.php}     <==> 用报警设置
	         {disable_alarm.php}    <==> 关闭报警
	         {show_alarm_log.php}   <==> 显示报警列表
	         {remove_alarm_log.php} <==> 删除某个报警记录
	
2017-07-10 本次更新内容：

	#1接口{trace.php}请求返回信息更改
	#2新增接口:
	         {trace_my.php}   <==> 显示所有设备的坐标信息和围栏信息
	         
2017-07-19 本次更新内容：

	#1接口{trace.php}|{trace_my.php}新增返回参数【imei】【status】【temper】【gps】【gsm】
	#2新增接口:
            {sensor_status_statistics.php} <==> 首页设备状态统计 
            {show_alarm_setting.php}       <==> 显示报警设置信息
            
2017-07-25 本次更新内容
	
	#1规范部分接口
	#2新增token令牌验证机制，在请求的时候需多传【userid】【token】两个参数，之前有的不需要，先统一一下用【userid】，之前是【uid】的需改下在初步涉及接口有:
				{validate_user.php}
				{trace.php}
				{trace_my.php}
				{path_back.php}
				{bind_sensor.php}
				{unbind_sensor.php}
				{journey_statistics.php}
				{electric_fence.php}
				{discard_electric_fence.php}
				{change_nick.php}
				{show_sensor.php}
	 