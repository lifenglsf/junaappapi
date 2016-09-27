| 接口名称        | 接口地址           | 接口参数  |接口方式|header|response|
| ------------- |-------------| -----|----|----|-----|
| 用户注册      | {域名}/juna/user/register.json | name:手机号，pass：密码，code：手机验证码 |post|X-CSRF-Token:XXX，token的值来自于{域名}/services/session/token|401:csrf fail <br/>406：缺少注册信息或手机验证码相关错误<br/>200:成功|
| 用户登录      | {域名}/juna/user/login.json      |name:手机号，pass:密码 |post|X-CSRF-Token:XXX，token的值来自于{域名}/services/session/token|401:csrf fail或用户名密码错误,403：用户未启用，406：用户已登录|
| 创建手机验证码 | {域名}/juna/user_interface/add_mobilecode.json|name：手机号|post|X-CSRF-Token:XXX，token的值来自于{域名}/services/session/token|401:csrf错误或者缺少参数，406：手机号码错误或者验证码发送失败|