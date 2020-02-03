---
title: 2019年1月13日 总结04 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## 项目总结
1.后端
1.调用接口获取登录凭证（code）。通过凭证进而换取用户登录态信息，包括用户的唯一标识（openid）及本次登录的会话密钥（session_key）等。
(接口:"https://api.weixin.qq.com/sns/jscode2session?" .
 "appid=%s&secret=%s&js_code=%s&grant_type=authorization_code"
接口配发参数请求参数!!!(这些参数都是由url中的get传参拼接发送出去的,这里用到%s的表达式)
使用这个方法对%s进行拼接$this->wxLoginUrl = sprintf(config('wx.login_url'), $this->wxAppID, $this->wxAppsecret, $this->code);
属性 类型 必填 说明 获取方式
appid string 是 小程序 appId 微信平台获取
secret string 是 小程序 appSecret 微信平台获取
js_code string 是 登录时获取的 code 微信平台获取
grant_type string 是 授权类型，此处只需填写 authorization_code 将这个type添加到了url中,位置在黄色处
2.向用户登录发送信息后返回值的接收并处理
获取token:
(1)返回值是json类型,使用json_decode转成数组
(2)判断返回值没有错误,就生成token令牌
(3)在用户表中使用openid查询是否有该openid的记录
(4)如果有就直接查询该用户的uid,如果没有就创建该user记录
(5)token令牌要放在缓存中,所以生成要存入缓存的数据,并在准备缓存数据的时候要加入用户权限标识
(6)生成token令牌,(主要就是随机数+md5加密+盐)
(7)设置config文件中设置token缓存过期时间为7200秒(建议设置7000)
(8)存入缓存使用cache方法(参数1是存入的键,参数2是存入的值,参数3是过期时间)
(9)因为cache方法的返回值是boolean类型,判断是否写入成功
(10)如果写入成功就返回token,如果失败就抛出错误
总结:该cache中的键是token的随机数,就是token令牌,value值就是将发给微信服务器的信息返回的信息,最终return回去的就是该缓存的token令牌,也就是键
校验token:
1.从校验接口接收到了前端发来的token令牌
2.从当前tp5提供的缓存那种读取是否有该token令牌
3.如果有就返回true,如果没有就返回false(如果返回了false前端就会向后端重新申请令牌)
属性 类型 说明
openid string 用户唯一标识
session_key string 会话密钥
unionid string 用户在开放平台的唯一标识符，在满足 UnionID 下发条件的情况下会返回，详见 UnionID 机制说明。
errcode number 错误码
errmsg string 错误信息
errcode 的合法值
值 说明 最低版本
-1 系统繁忙，此时请开发者稍候再试 
0 请求成功 
40029 code 无效 
45011 频率限制，每个用户每分钟100次 

2.前端
1.为了用户一登录就能获取token令牌证明自己的身份,我们将token的获取方法放入app.js文件中的onLoad的中
2.app.js中的方法:获取缓存中的token键的令牌,如果有就校验是否是否过期,没有就申请一个token,
获取token令牌:
1.向获取token令牌发送code值(code值在wx.log()方法中的success的回调res参数中)
校验token令牌:
1.将token发送到服务端的校验令牌接口,进行校验,并返回成功或失败(boolean值),如果是真就校验成功,如果是假就向后端申请新的token令牌











