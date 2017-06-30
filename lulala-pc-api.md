register_mobileno.php <==> 注册手机号 <==> request: post
	
	receive: 	
			string		mobileno	<==> 手机号码
			string		note		<==> 短信验证码
			string		company		<==> 公司名称（可选：企业注册必需）
			string		code		<==> 邀请码（可选，暂时不必填）
	return:
			success	<==> { errno: 0, errmsg: '', data: xx }
			errno	<==> { errno: 4031, errmsg: '验证码错误' }
				     { errno: 4041, errmsg: '用户已注册' }
				     { errno: 4033, errmsg: '创建账号失败' }
				     { errno: 500, errmsg: '服务器错误' }
						 
register_additional.php <==> 设置额外信息(创建密码) <==> request: post
	
	receive:
			int			uid			<==> 用户id
			string		name		<==> 用户名
			string		passwd		<==> 密码
	return:
			success <==>	{ errno: 0, errmsg: '', data: xx }
			errno	<==>    { errno: 4031, errmsg: '设置密码失败' }
