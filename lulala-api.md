send_sms.php  <==>  发送短信验证码   <==>  request: post
	
	receive: 
			string  phone  <==> 手机号码
	return:
			success  <==> { errno: 0, errmsg: "" }
			failed   <==> { errno: 4031, errmsg: 短信发送失败 }
	
register.php  <==>  注册第一步  <==> request: post

	receive:
			string mobile  <==> 手机号码
			number note    <==> 短信验证码
	return:
			success  <==> { errno: 0, errmsg: "" data: ['userid': xx] }
			failed   <==> { errno: 4031, errmsg: 验证码错误 },
			              { errno: 4041, errmsg: 用户已注册 },
			              { errno: 4032|4033|4034, errmsg: 用户注册失败 },
			              { errno: 500, errmsg: 服务器异常 }
			              
set_password.php  <==>  注册第二步|修改密码第二步, 设置密码 <==> request: post

	receive:
			int    userid   <==> 用户id
			string password <==> 密码
	return:
			success  <==> { errno: 0, errmsg: "" } 
			failed   <==> { errno: 4031, errmsg: 设置密码失败 }
			
login.php  <==>  登录 <==> request: post

	receive:
			string  mobile   <==> 手机号码
			string  password <==> 密码      【可选, 普通登录必需】
			number  note     <==> 短信验证码 【可选, 快速登录必需】
			string  token    <==> 设备标识符  
	return:
			success  <==> { errno: 0, errmsg: "", data: ['userinfo': xx, 'encryptinfo': xx, 'sessionid': xx, 'token': xx] }(如果有token,即此设备为要被踢下)
			failed   <==> { errno: 4031, errmsg: 验证码错误 },
			              { errno: 404, errmsg: 用户不存在 },
			              { errno: 4032, errmsg: 密码错误 }
			            
validate_user.php <==> 修改密码第一步, 验证用户信息 <==> request: get

	receive:
			string  mobile <==> 手机号码
			number  note   <==> 短信验证码
	return:
	   		success  <==> { errno: 0, errmsg: "", data: ['userid': xx] }
	   		failed   <==> { errno: 4031, errmsg: 验证码错误 },
	   		              { errno: 404, errmsg: 用户不存在 } 
logout.php  <==> 退出登录 <==> request: post
	
	receive:
			int    userid  <==> 用户id
		
	return:
			success <==> { errno: 0, errmsg: ""}
			failed  <==> { errno: 404, errmsg: 用户不存在 },
							{ errno: 500, errmsg: 服务器错误}
			