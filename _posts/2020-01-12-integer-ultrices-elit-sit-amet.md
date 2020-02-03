---
title: 2019年1月12日 总结03
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## 项目总结
一、banner图
1.后端
(1)根据数据库我们知道接口只需要一个id值就可以根据这个id值去查询banner表确定banner位置,
(2)根据banner表与banneritem表使用hasMany建立关联,让banner表的id与banneritem中的banner_id进行关联,再通过banneritem表中的img_id与image表的id建立关联,这样就得到了image表中的image的url参数
(3)建立关联后可以建立查询的方法,查询出banner图使用的url,然后在banner的model方法中也建立关联查询方法, 查询语句:$banner=self::with(['与banneritem建立连接的方法名','与image建立关联的方法名'])->find($id);
(4)在接口调用model中的查询方法
1.前端
注意:由于前端也应用于MVC架构,所以也会有M的业务层出现
(1)在home.js文件中调用home-model.js文件的getBannerData方法,两个参数为:参数1是id号,参数2是回调箭头函数(在getBannerData方法调用执行之后将箭头函数的值返回再执行箭头函数中的值)
    home.getBannerDate(id,(res)=>{
      //数据绑定
      this.setData({
        'bannerArr': res
      });
    });
(2)home-model.js文件中的getBannerData方法如下:执行流程是先复制给params对象,再执行基类中的request方法(由于继承了base基类,所以可以直接this.的方式去调用)
  getBannerDate(id,callback){
    var params={
      url:'banner/'+id,
      scallback:function(res){
        callback&&callback(res.items);
      }
    }
    this.request(params)
  }
(3)base文件中的request方法主要是向后端接口发送请求,并且接受回传














