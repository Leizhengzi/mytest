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
				
sensorShow($userid, $imei, $groupid, $page, $spage) <==> 显示设备列表 method: get

		receive:
				int		$userid <==> 用户id 例：89776
				string	$imei   <==> 设备号 例：333333333333333
				int		$groupid <==> 分组id
				int		$page <==> 页码数
				int 	$spage <==> 每页显示函数
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: [{
						id: 900398,
						createtime: "2017-08-03 13:23:30",
						imei: "695502000001144",
						imsi: "460040300601504",
						device_type: LQ1, 设备类型
						mobel: 宝马, 车辆类型
						seqno: 2132132u13u21i, 车牌号码
						auto_insurance: 2017-09-11, 车辆保险
						frame_number: WDu23ui4, 车架号
						address: 详细地址
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
				
removeBinding($userid, $sensorid) <==> 删除设备 method: post

		receive:
				int		$userid   <==> 用户id 例: 821932
				int		$sensorid <==> 设备id 例: 899843
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				fail: {
					errno: 403, errmsg: "删除设备失败"
				}
				
register($mobile, $note, $cookieid, $company, $invationCode = null) <==> 验证注册信息 method: get

		receive:
				string	$mobile <==> 手机号 例: 15514790089
				int		$note   <==> 短信验证码 例: 2341
				string	$cookieid <==> cookie信息 例: dfkajflaidaskfd
				string	$company <==> 公司名称 例: 科技有限公司
				string	$invationCode <==> 邀请码
		return: 
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				fail: {
					errno: 4031, errmsg: "验证码错误"
					errno: 403, errmsg: "手机号或公司已注册"
				}
				
SetPassword($mobile, $password, $app, $name, $email, $company) <==> 注册用户信息入库 method: post

		receive:
				string $mobile <==> 手机号 例: 15514790089
				string	$password <==> 密码 例: xxxxxxx
				string	$app <==> 应用常量 例: pc
				string	$name <==> 姓名 例: 张三
				string	$email <==> 邮箱 例: zhangsan@outlook.com
				string	$company <==> 公司名称 例: 科技有限公司
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: { 910291 } // 用户id
				}
				fail: {
					errno: 4034, errmsg: 创建密码失败
					errno: 500, errmsg: 注册时发生服务器内部错误
				}

getSensorStatusStatistics($uid, $imei = null) <==> 获取不同状态的设备统计列表 method: get

		receive:
				int		$uid <==> 用户id 例: 89212
				string	$imei <==> 设备号 例: 333333333333333
		return:
				success: {
					errno: 0,
					errmsg: "",
					data:{
						{
							all: {"imeis":["333333333333333"...],"count":8},
							online: {"imeis":[],"count":0}
							off: {"imeis":[],"count":0}
							malf: {"imeis":[],"count":0}
						}
					}
				}
				
groupAdd($userid, $name) <==> 添加分组 method: post

		receive:
				int		$userid <==> 用户id 例: 89123
				string	$name <==> 分组名称 例: LQ1
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				fail: {
					errno: 403, errmsg: 分组已添加，不能重复添加
					errno: 500, errmsg: 服务器内部错误
				}
				
groupChange($userid, $groupid, $name) <==> 分组修改 method: post

		receive:
				int		$userid <==> 用户id 例: 891234
				int 	$groupid <==> 分组id 例: 21314
				string	$name <==> 分组名称 例: LQ1
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				fail: {
					errno: 4031, errmsg: 分组名称已存在
					errno: 4032, errmsg: 修改分组名称失败
				}
				
groupRemove($groupid) <==> 删除分组 method: post

		receive:
				int 	$groupid <==> 分组id 例: 123213
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: {321421} // 分组id
				}
				fail: {
					errno: 403, errmsg: 删除分组失败
				}
				
getSensorsFromGroup($userid) <==> 分组列表显示 method: get

		receive:
				int 	$userid <==> 用户id 例: 82913
		return: 
				success: {
					errno: 0,
					errmsg: "",
					data: [
						98231:{
							imeis: [{
								sensorid: 321312,
								imei: 695502000001144
							}..]
							name: W-X1设备
						}...]|[]
				}

			
getUngroupedSensors($uid, $imei = null) <==> 显示未分组的设备列表 method: get

		receive:
				int		$uid <==> 用户id 例: 43123
				string	$imei <==> 设备imei号 例: 333333333333333 支持模糊搜索
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: [{
						sensorid: 892136,
						imei: 333333333333333
					},...]|[]
				}
				
sensorUpdate($sensorid, $imsi, $mobel, $autoinrs, $seqno, $framenum, $remark) <==> 修改设备信息 method: post

		receive: 
				int		$sensorid <==> 设备id 例:728194
				string	$imsi <==> 物联网卡号 例:460040300601505
				string	$mobel <==> 车辆类型 例: 宝马X5
				string	$autoinrs <==> 车辆保险 例: 2017-08-20
				string	$seqno <==> 车牌号码 例: 460040300601505
				string	$framenum <==> 车架号 例: LQ123213213
				string	$address <==> 详细地址 例: xxxx
		return:
			 	success {
					errno: 0,
					errmsg: "",
					data: []
				}
				failed: {
					errno: 4031, errmsg: 修改imsi失败
					errno: 4032, errmsg: 修改车辆信息失败
					errno: 500, errmsg: 服务器错误
				}
				
addSensorToGroup($groupid, array $sensorid) <==> 分配设备到分组中 method: post

		receive:
				int 	$groupid <==> 分组id 例: 892182
				array	$sensorid <==> 设备id集合 例: [394019,3820184]
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				failed: {
					errno: 500,
					errmsg: 服务器错误
				}
				
removeSensorFromGroup($userid, $sensorid) <==> 删除组内的设备 method: post

		receive: 
				int 	$userid <==> 用户id 例: 89218
				int		$sensorid <==> 设备id 例: 89131
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				failed: {
					errno: 403,
					errmsg: 删除失败
				}
		
employeeAdd($companyid, $mobileno, $name, $address) <==> 员工添加 method: post

		receive:
				int		$companyid <==> 公司id 例: 12345
				int 	$mobileno <==> 手机号 例: 12345678098
				string	$name <==> 姓名 例: 张三
				string	$address <==> 地址 例: 北清路
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				failed: {
					errno: 4030, errmsg: 员工已添加，不能重复添加
					errno: 500, errmsg: 服务器错误
					
				}
	
employeeRemove($emp_id) <==> 员工删除 method: post

		receive:
				int		$emp_id <==> 员工id 例: 1232132
		return:
				success: {
					errno: 0,
					errmsg: "",
					data: []
				}
				failed: {
					errno: 500, errmsg: 服务器错误
				}
				
employees($userid) <==> 显示员工列表 method: get
		
		receive: 
				int		$userid <==> 当前登录账号id
		returen:
				success: {
					errno: 0,
					errmsg: "",
					data: {xxxx}
				}
				
			