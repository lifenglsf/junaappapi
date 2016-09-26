| 地址        | 接口说明  | 接口方法  | 接口参数 |接口header|content type|接口返回|             
|:----------:|:--------：|:---------：|:---------: |---------|--------|--------|
| {域名}/juna/user/register.json| 用户注册 | post |name:手机号，pass：密码，code：手机验证码|X-CSRF-Token:XXX，token的值来自于{域名}/services/session/token|-| 401:csrf fail <br/>406：缺少注册信息或手机验证码相关错误<br/>200:成功<br/>|
|{域名}/juna/user_interface/add_mobilecode.json | 创建手机验证码 | post |name:手机号|X-CSRF-Token:XXX，token的值来自于{域名}/services/session/token|application/json|401:csrf fail <br/>406：手机号不存在或者验证码创建失败<br/>200:成功<br/>|
| zebra stripes | are neat      |    $1 |

|| *Year* || *Temperature (low)* || *Temperature (high)* ||
|| 1900 || -10 || 25 ||
|| 1910 || -15 || 30 ||
|| 1920 || -10 || 32 ||


|| *aaaaa* || *bbbbb* ||
|| 123 || kkdfsdf ||