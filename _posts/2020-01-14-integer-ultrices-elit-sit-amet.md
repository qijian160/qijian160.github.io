---
title: 2019年1月14日 总结05 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## 项目总结
1.后端
查询地址信息:
1.在token中获取到uid
2.通过uid从userAddress表中查询出用户的id
3.如果有就直接返回给前端,没有就抛出错误
创建地址信息:
1.在token中获取uid
2.使用uid在user表中查询出openid
3.如过没有就抛出错误,如果有就使用(input("post."))的方式接收前端传来的address信息,
4.通过uid在address表中查询,如果查到了就更新数据,如果没有查到就新增数据,如下可见:更改数据$user->address表名     而新增数据就是$user->address与user表建立关联的方法
更新数据:$user->address->save($dataArray);
新增数据:$user->address()->save($dataArray);
5.返回给前端
2.前端
1.在进入订单页的时候要从后端读取地址信息,显示出来,如果没有就点击地址信息框触发单击事件
2.通过微信API接口获取地址信息 wx.chooseAddress
3.将获取到的信息进行数据绑定
4.将地址信息保存到数据库中
Object object
属性 类型 默认值 必填 说明
success function  否 接口调用成功的回调函数
fail function  否 接口调用失败的回调函数
complete function  否 接口调用结束的回调函数（调用成功、失败都会执行）
object.success 回调函数
参数
Object res
属性 类型 说明
userName string 收货人姓名
postalCode string 邮编
provinceName string 国标收货地址第一级地址
cityName string 国标收货地址第二级地址
countyName string 国标收货地址第三级地址
detailInfo string 详细收货地址信息
nationalCode string 收货地址国家码
telNumber string 收货人手机号码
errMsg string 错误信息








