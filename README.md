| 接口名称        | 接口地址           | 接口参数  |接口方式|header|status code|
| ------------- |-------------| -----|----|----|-----|
| 用户注册      | http://api.junashare.com/juna/user/register.json | name:手机号必填，pass：密码必填，code：手机验证码必填 |post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|401,406,200|
| 用户登录      |http://api.junashare.com/juna/user/login.json      |name:手机号必填，pass:密码必填 |post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|401,403,406,200|
| 创建手机验证码 | http://api.junashare.com/juna/user_interface/add_mobilecode.json |name：手机号必填|post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|401,406,200|
| 用户登出      | http://api.junashare.com/juna/user/logout.json | 无 |post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token，cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值|401，406,200|
| 易购商品列表      | http://api.junashare.com/juna/product.json | page:页码 ,time：时间段，有效值为0,1,2,3,4|get|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|406,200，返回数据中data为产品信息，timeperiod为时间段信息，selected为1为选中的时间段|
| 享什么商品列表      | http://api.junashare.com/juna/share_product.json | page:页码必填,time：时间段非必填，有效值为0,1,2,3,4|get|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|406，200，返回数据中data为产品信息，timeperiod为时间段信息，selected为1为选中的时间段|
| 商品详情      | http://api.junashare.com/juna/product/商品id/detail.json | 无 |get|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|406,200，返回数据中product为商品信息，seller为商家信息|
| 加入盒子      | http://api.junashare.com/juna/product/addtobox.json | nid：商品id必填 services_token:XXX必填，token的值来自于 http://api.junashare.com/services/session/token|post|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值|403,406,200|
| 盒子列表      | http://api.junashare.com/juna/boxlist.json | services_token:XXX必填，token的值来自于 http://api.junashare.com/services/session/token |get|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值|403,,200|
| 购买商品      | http://api.junashare.com/juna/product/buy.json | nid：商品id必填 ,services_token:XXX必填，token的值来自于 http://api.junashare.com/services/session/token|post|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值|403,406,200|
| 广告      | http://api.junashare.com/juna/banner.json |btype:banner类型必填，1为享什么的banner，2为易购的banner|get|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|406,200|
| 移出盒子商品      | http://api.junashare.com/juna/product/removefrombox.json | nid：商品id必填 ,services_token:XXX必填，token的值来自于 http://api.junashare.com/services/session/token|post|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值|403,406,200|
| 用户信息认证      | http://api.junashare.com/juna/user_interface/user_cert.json | username：姓名必填 ,companyname:公司名称必填，companyaddress:公司地址必填，cert:图片file的名字必填，certtype:认证类型必填，有效值为1名片，2工牌，3在职证明，services_token:XXX必填，token的值来自于 http://api.junashare.com/services/session/token|post|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值,Content-Type:multipart/form-data|403,406,500,200|
| app需要的支付数据      | http://api.junashare.com/juna/orders/pre_pay.json | orderid必填:订单id ,payment_type必填:支付类型，1为支付宝，2为微信认，services_token:XXX必填，token的值来自于 http://api.junashare.com/services/session/token|post|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值,Content-Type:multipart/form-data|406,500,200|
| 校验app支付是否成功      | http://api.junashare.com/juna/orders/app_payment_callback.json | orderid必填:订单id ,payment_type必填:支付类型，1为支付宝，2为微信认，services_token:XXX必填，token的值来自于 http://api.junashare.com/services/session/token|post|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值,Content-Type:application/json|406,200|
| 用户注册 v0.2.1     | http://api.junashare.com/juna/junausers/register.json | name:手机号必填，pass：密码必填，code：手机验证码必填 |post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|401,406,200|


|http 状态码|信息|
|----------|---|
|200|成功|
|401|token错误<br/>缺少参数xxx<br/>错误的验证码<br/>用户名或密码错误|
|403|用户名 XXX 尚未激活或已被屏蔽。|用户未登录
|406|用户未登录<br/>已作为XXX登录<br/>验证码已失效<br/>手机号码错误<br/>手机验证码已使用，请重新获取<br/>手机验证码不能为空<br/>错误的验证码<br/>不支持的商品类型<br/>商品未发布<br/>商品不存在<br/>商品id都不能为空<br/>商品限时结束<br/>盒子已满，请先从盒子中删除部分商品<br/>此商品已加入盒子，不能重复加入<br/>商品已下架<br/>商品已售罄<br/>商品今天已购买<br/>你未收藏此商品<br/>商品时间段错误<br/>banner类型错误<br/>只能上传图片<br/>认证图片不能为空<br/>支付数据异常<br/>订单id错误<br/>手机号用户已存在|
|500|未知错误|

|商品字段|商品字段描述|
|------|-----|
|title|商品名称|
|nid|商品id|
|type|product：一购商品，share_product：享什么商品|
|body.und.0.value|商品描述|
|field_price.und.0.value|一购价格|
|field_origin_price.und.0.value|享什么价格，市场价|
|field_total_num.und.0.value|商品总数|
|field_pictures.und.0.uri|图片原图路径，可以有多个图片，第二个图片地址field_pictures.und.1.uri|
|field_pictures.und.0.thumb|缩略图，可以有多个图片，第二个图片地址field_pictures.und.1.thumb|
|field_inbox_num.und.0.value|加入盒子数量|
|field_image_for_list.und.0.uri|列表页图片|
|field_description.und.0.value|商品描述|
|field_image_for_box.und.0.uri|一购商品盒子列表图片|
|isinbox|是否在盒子中1代表已经在盒子中|

|我的盒子字段|我的盒子字段描述|
|---|---|
|nid|商品id|
|product_type|商品类型  product：一购商品，share_product：享什么商品|
|inbox_num|加入盒子数量|
|remain_num|剩余数量|
|field.und.0.thumb|商品缩略图|
|remain_boxproduct_num|还可放入盒子的商品数量|

|订单字段|订单字段描述|
|---|---|
|id|订单id|
|nid|商品id|
|product_type|商品类型  product：一购商品，share_product：享什么商品|
|created|订单创建时间|
|uid|购买或申领用户id|
|amount|商品数量|
|price|商品单价|
|total_price|订单金额|
|alipay_order_id|支付宝订单号|
|status|订单状态|
|express_id|物流编号|
|payment_type|付款方式|
