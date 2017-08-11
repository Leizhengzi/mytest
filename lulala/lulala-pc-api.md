getSensorJourney($sensorid, $start, $end) <==> 获取设备里程信息列表  method: get

	receive:
			int		$sensorid <==> 设备id 例：900891
			date	$start    <==> 查询区间开始日期 例：2017-08-09
			date	$end      <==> 查询区间结束日期 例：2017-08-09
	return: 
			success: { 
				errno: 0, 
				errmsg: "", 
				data:[{
					sensorid: 89100,
					date: 2017-08-09 13:22:24,
					distance: 0.327,
					imei: 33333333333333
				},...]|[] 
			}
			
changePasswordWithMobile($mobileno, $cookieid, $note, $password) <==> 根据手机号修改密码 method: post
	
		receive:
				string		$mobileno <==> 手机号 例：18603911401
				string		$cookieid <==> cookeid 
				string		$note     <==> 短信验证码 例：1234
				string		$password <==> 密码 例：xxxxxxxx
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				fail: {
					errno: 403, errmsg: "验证码错误"
					errno: 404, errmsg: "无效的手机号"
					errno: 500, errmsg: "服务器内部错误"
				}
				
bindEmail($userid, $email) <==> 绑定邮箱 method: post

		receive: 
				int		$userid <==> 用户id 例：89776
				string	$email  <==> 邮箱 例：1551001@qq.com
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				fail: {
					errno: 403, errmsg: "绑定邮箱失败"
				}
				
sensorShow($userid, $imei) <==> 显示设备列表 method: get

		receive:
				int		$userid <==> 用户id 例：89776
				string	$imei   <==> 设备号 例：333333333333333
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: [{
						id: 900398,
						createtime: "2017-08-03 13:23:30",
						updatetime: "2017-08-03 13:23:30",
						imei: "695502000001144",
						model: "jiawei",
						imsi: "460040300601504",
						nextver: 0,
						flag: 0,
						status: N,
						is_reboot: N,
						is_upgrade: N,
						device_type: LQ1
					}]|[]
				}
				
personalChange($userid, $name, $qq, $avatar) <==> 修改个人信息 method: post

		receive:
				int		$userid <==> 用户id 例：896776
				string	$name   <==> 姓名 例：张三
				string	$qq     <==> QQ号
				string	$avatar <==> 头像 例：http://url.path/avatar.png
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				fail: {
					errno: 403, errmsg: "修改姓名失败|修改基本信息失败"
					errno: 500, errmsg: "服务器内部错误"
				}
				
personalShow($userid) <==> 个人信息显示 method: get

		receive:
				int		$userid <==> 用户id 例：896766
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: {
						name: 张三,
						userid: 896776,
						avatar: http://url/avatar.png
						mobileno: 1551447089
						qq: 150813213
						emal: zhangsan@outlook.com
					}|[]
				}