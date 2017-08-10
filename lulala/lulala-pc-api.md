getSensorJourney($sensorid, $start, $end) <==> 获取设备里程信息列表  method: get

	receive:
			int 		sensorid <==> 设备id 例：900891
			date     	start    <==> 查询区间开始日期 例：2017-08-09
			date		end      <==> 查询区间结束日期 例：2017-08-09
	return: 
			success: { 
				errno: 0, 
				errmsg: "", 
				data:{[
					sensorid: 89100,
					date: 2017-08-09 13:22:24,
					distance: 0.327,
					imei: 33333333333333
				],...|[]} 
			}
			
changePasswordWithMobile($mobileno, $cookieid, $note, $password) <==> 根据手机号修改密码 method: post
	
		receive:
				string		mobileno <==> 手机号 例:18603911401
				string		cookieid <==> cookeid 
				string		note     <==> 短信验证码 例: 1234
				string		password <==> 密码 例: xxxxxxxx
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