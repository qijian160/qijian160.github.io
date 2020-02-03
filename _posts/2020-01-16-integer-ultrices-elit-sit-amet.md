---
title: 2019年1月16日 总结07 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## 项目总结
前端:
跳转到订单页的时候,分别是在"我的"页面中跳转和一个在购物车页面跳转,要进行区分,所以再跳转的时候附加一个from值,标记是从"我的"页面跳转的还是在购物车页面跳转,
为什么区分?
因为在购物车跳转到订单页的时候,订单的信息是在wx.setStorageSync缓存中读取的,而在"我的"页面跳转就要在数据库中读取
1.当进入到订单也的时候在onload中接收跳转的传参,判断是从购物车跳转的还是在"我的"页跳转的,
在购物车跳转:	
1)在购物车跳转来的就要在wx.setStorageSync缓存中读取订单数据,形成订单数据,接收购物车传来的商品数量,及初始化定义订单状态,如:orderStatus,在address的model类中获取到地址信息,
2)进行微信支付,单击去支付按钮触发单击事件,单击事件首先进行,地址是否填写的判断,如果填写了就正常支付,如果没填写就弹框报错,
3)正常支付,判断orderStatus(订单状态)如果是0就代表购物车下单,是第一次支付,第一次支付就需要进行对数据库的下单操作,如果不是0就代表是在"我的"页跳转,就是在数据库中读取的,就不需要对数据库进行下单操作,因为数据库中已经有了订单,
4)当前orderStatus是0,进行首次支付,获取商品信息,对商品信息进行遍历,将商品的id以及数量遍历到orderInfo(订单信息)中
5)进行向数据库下单操作,判断下单是否成功,如果下单失败则弹框提示下单失败并且携带相关信息,订单生成成功,首先将从数据库回调的订单id进行赋值,在支付时使用
6)进行支付,将订单id传入支付方法,向自己编写的支付API接口发送请求,并携带id,
7)判断回传信息中是否有下单时间戳,如果没有就代表支付失败没有该订单则给回调函数传参为0表示支付失败
8)请求成功就将回传信息传入回调函数,调用微信官方提供的前端支付API接口,携带的参数查看官方文档,都在请求成功的回传信息中,
9)如果接口调用成功走success则给回调函数传参,为2表示支付成功,失败走fail则给回调函数传参1表示支付失败,与上边的0相对应
10)将下单支付的商品在购物车中移除,并且做一个支付成功的标记变量,传入支付结果页,
11(支付结果也接到传参后判断,该页显示支付成功或支付失败
在我的页跳转:	
1)在判断不是在购物车页跳转后,直接对订单id进行数据绑定,
2)通过订单id向后端订单接口请求,查询出此订单的信息,进行回传到回调函数中,
3)进行订单信息的数据绑定
4)
Object object
属性 类型 默认值 必填 说明
timeStamp string  是 时间戳，从 1970 年 1 月 1 日 00:00:00 至今的秒数，即当前的时间
nonceStr string  是 随机字符串，长度为32个字符以下
package string  是 统一下单接口返回的 prepay_id 参数值，提交格式如：prepay_id=***
signType string MD5 否 签名算法
paySign string  是 签名，具体签名方案参见 小程序支付接口文档
success function  否 接口调用成功的回调函数
fail function  否 接口调用失败的回调函数
complete function  否 接口调用结束的回调函数（调用成功、失败都会执行）
object.signType 的合法值
值 说明 最低版本
MD5 MD5 
HMAC-SHA256 HMAC-SHA256 
后端:
Loader::import('WxPay.WxPay', EXTEND_PATH, '.Api.php');引入接口文件,如果没有去手册下载SDK,继承\WxPayNotify
1.在自己编写的API支付接口实例化一个支付的业务处理类,然后并且传入订单id
2.支付的业务处理页中,构造方法中接收订单id,判断订单id是否为空,如果为空就抛出错误
3.编写业务方法,根据传入的订单id,在数据库查询出订单信息
4.检测订单中的uid与token令牌中当前用户的uid是否一致,检测订单状态是否是未支付状态,如果都正确返回 true
5.检测库存,检查订单状态(总金额等)如果没有问题,则生成预订单
6.生成预订单,实例化微信提供的服务端支付API接口类,在token中获取openid.传入生成预订单方法刚刚获取的订单状态的一系列参数(总金额等)
7.进行给微信服务器统一下单,使用实例化的支付对象,使用里边的方法设置统一下单需要的参数,也可以在这个网站查询https://pay.weixin.qq.com/wiki/doc/api/jsapi.php?chapter=9_1
参数1:使用实例化的支付对象的SetOut_trade_no方法设置订单号
例子:$wxOrderData = new \WxPayUnifiedOrder();
$wxOrderData->SetOut_trade_no($this->orderNO);
参数2:使用实例化的支付对象的SetTrade_type方法设置为JSAPI(这个是微信提供的)
参数3:使用实例化的支付对象的SetTotal_fee设置支付总金额
参数4:使用实例化的支付对象的SetBody方法设置小程序名称(一般都用自己的产品名)
参数5:使用实例化的支付对象的SetOpenid设置openid
参数6:使用实例化的支付对象的SetNotify_url设置微信服务器回调信息的接收地址(用服务器测试,必须是公网IP,让微信服务器能够找到你)
8.在统一下单最后生成完了订单所需的参数给实例化的支付对象,可以将该对象传入设置签名方法,
9.调用统一下单,将实例化的支付对象,使用一下方法,传入支付API的unifiedOrder方法,如果实例化的支付对象['return_code']!=SUCCESS或实例化支付对象['return_code']!=SUCCESS有一个不是SUCCESS就是统一下单调用成功,
		$wxOrder=\WxPayApi::unifiedOrder($wxOrderData);
10.再次检测检测订单中的uid与token令牌中当前用户的uid是否一致,检测订单状态是否是未支付状态,如果都正确返回 true
11.生成签名,实例化对象$jsApiPayData=new \WxPayJsApiPay();使用该对象设置参数
$jsApiPayData->SetAppid(app_id)
$jsApiPayData->SetTimeStamp(设置时间戳)
$jsApiPayData->SetNonceStr(随机字符串)
$jsApiPayData->SetPackage('prepay_id='.$wxOrder['prepay_id'])     !!!这里设置必须使用'prepay_id='.$wxOrder['prepay_id'];的语法,比较特殊,prepay_id就是要发给用户的一些东西
$jsApiPayData->SetSignType(加密方式)
$sign=$jsApiPayData->MakeSign();
12.因为客户端需要的是一组数据,要将jsApiPayData对象转换成为数组,使用该方法转为数组			$rawValues=$jsApiPayData->GetValues();
13.将生成的标签,赋值给该数组的paysign的位置
$rawValues['paySign']=$sign;
14.删除不需要传送到客户端的信息,unset(appid)
15.return返回$rawValues

回调支付信息:
Loader::import('WxPay.WxPay', EXTEND_PATH, '.Api.php');引入接口文件,如果没有去手册下载SDK,继承\WxPayNotify
1.重写NotifyProcess方法接收参数为(data,&msg),data是回传回来的参数,msg是如果回调失败,回调失败的信息将存储在这里
2.如果$data['result_code'] == 'SUCCESS'就进入事务锁中,根据data中的订单号,查询出订单信息,
3.检查库存,如果库存满足就修改订单状态,并且减少库存,如果不满足就修改订单状态但是不减少库存
4.返回true,
注意:无论最终出现什么错误都要返回true,否则会不断的接收到微信服务器发来的回调通知
5.在自己编写的回调接口中调用时候,要使用handle方法调用,$notify->handle();这样才能获取到NotifyProcess方法中的data参数

