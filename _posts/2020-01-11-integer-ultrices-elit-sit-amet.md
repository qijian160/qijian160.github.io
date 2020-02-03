---
title: 2019年1月11日 总结02 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## 项目总结
联表查询方法:
这是banner的model类中的两个方法,一个是跟bannerItems的model类建立联系,第二个是获取banner在img表中的数据,
因为banner与banneritems表中了关联,banneritems表中编写了img方法,这样就可以直接用banner与bannerItems的方法名直接去.img的方法去获取img表中的数据
public function items(){
    return $this->hasMany('BannerItem','banner_id','id');
}
public static function getBannerByID($id){
//简单意思就是通过以items.img为标准查询image表中的数据
      $banner=self::with(['items','items.img'])->find($id);
    //$banner=self::with(['与banneritem建立连接的方法名','与image建立关联的方法名'])->find($id);
      return $banner;
}





