| 接口名称        | 接口地址           | 接口参数  |接口方式|header|status code|
| ------------- |-------------| -----|----|----|-----|
| 用户注册      | http://api.junashare.com/juna/user/register.json | name:手机号，pass：密码，code：手机验证码 |post|X-CSRF-Token:XXX，token的值来自于{域名}/services/session/token|401,406,200|
| 用户登录      |http://api.junashare.com/juna/user/login.json      |name:手机号，pass:密码 |post|X-CSRF-Token:XXX，token的值来自于{域名}/services/session/token|401,403,406,200|
| 创建手机验证码 | http://api.junashare.com/juna/user_interface/add_mobilecode.json |name：手机号|post|X-CSRF-Token:XXX，token的值来自于{域名}/services/session/token|401,406,200|
| 用户登出      | http://api.junashare.com/juna/user/logout.json | 无 |post|X-CSRF-Token:XXX，token的值来自于{域名}/services/session/token|401，406,200|





|http 状态码|信息|
|----------|---|
|200|成功|
|401|token错误<br/>缺少参数xxx<br/>错误的验证码<br/>用户名或密码错误|
|403|用户名 XXX 尚未激活或已被屏蔽。|
|406|用户未登录<br/>已作为XXX登录<br/>验证码已失效<br/>手机号码错误<br/>手机验证码已使用，请重新获取<br/>手机验证码不能为空<br/>错误的验证码|