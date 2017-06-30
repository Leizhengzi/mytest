register_mobileno.php <==> 注册手机号 <==> request: post
	
	receive: 	
			string		mobileno  <==> 手机号码
			string		note      <==> 短信验证码
			string		company   <==> 公司名称（可选：企业注册必需）
			string		code      <==> 邀请码（可选，暂时不必填）
	return:
			success   <==> { errno: 0, errmsg: '', data: xx }
			fail      <==> { errno: 4031, errmsg: '验证码错误' }
			               { errno: 4041, errmsg: '用户已注册' }
			               { errno: 4033, errmsg: '创建账号失败' }
			               { errno: 500,  errmsg: '服务器错误' }
						 
register_additional.php <==> 设置额外信息(创建密码) <==> request: post
	
	receive:
			int       uid     <==> 用户id
			string    name    <==> 用户名
			string    passwd  <==> 密码
			string    email   <==> 邮箱
	return:
			success  <==>  { errno: 0, errmsg: '', data: xx }
			fail     <==>  { errno: 4031, errmsg: '设置名字失败' }
			               { errno: 4032, errmsg: '设置邮箱失败' }
			               { errno: 4033, errmsg: '设置密码失败' }
			               { errno: 500,  errmsg: '服务器错误' }
			
			
send_code.php <==> 发送短信验证码 <==> request: get

	receive:
			string    mobileno  <==> 手机号码
	return:
			success  <==> { errno: 0, errmsg: '' }
			fail     <==> { errno: 400/!0, errmsg: 发送验证码失败 }
			
validate_form.php <==> 修改密码(忘记密码)	<==> request: post
	
	receive:
			string    mobileno  <==> 手机号码
			string    note      <==> 短信验证码
			string    password  <==> 密码
	return:
			success  <==> { errno: 0, errmsg: '' }
			fail     <==> { errno: 4031, errmsg: 验证码错误 }
			              { errno: 404,  errmsg: 用户不存在 }
			              { errno: 4032, errmsg: 修改密码失败 }
			              { errno: 500,  errmsg: 服务器错误 }
			             
validate.php <==> 登录验证 <==> request: post

	receive:
			string    mobileno  <==> 手机号码
			string    passwd    <==> 密码
	return:
			success  <==> { errno: 0, errmsg: '' }
			fail     <==> { errno: 404,  errmsg: '用户不存在' }
			              { errno: 4032，errmsg: '密码错误' }

reset_password.php <==> 重置密码 <==> post
	
	receive:
			int       uid       <==> 用户id
			string    original  <==> 原始密码   
			string    password  <==> 新密码
	return:
			success  <==> { errno: 0, errmsg: '' }
			fail     <==> { errno: 4031, errmsg: '原密码错误' } 
			              { errno: 4032, errmsg: '重置密码失败' }
			              
reset_mobileno <==> 重置手机号 <==> post
	
	receive:
			int       uid       <==> 用户id
			string    mobileno  <==> 手机号
			string    note      <==> 短信验证码
	return:
	       success  <==> { errno: 0, errmsg: '' }
	       fail     <==> { errno: 4031, errmsg: '验证码错误' }
	                     { errno: 4032, errmsg: '修改手机号失败' }
			          
			
			