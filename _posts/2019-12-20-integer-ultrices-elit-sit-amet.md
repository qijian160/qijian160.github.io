---
title: 2019年12月20 日报 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## 项目总结
	URL路径格式:
PathInfo:就是原生的地址写法
混合模式:就是路由与PathInfo的结合
强制使用路由模式:就是只能使用路由模式
定义路由:
在route文件下use think\Route就可以在下面书写路由了
Route::接收方式(自定义的路由,实际路径);
Route::get('api/:version/Banner/:id值(传参时可以直接在路由后边 /值 的形式去传参)','api文件夹/:版本号(就是控制器外层的V1文件夹).控制器名/方法名');
Route::get('api/:version/Banner/:id','api/:version.Banner/getBanner');
路由分组:
相当于在product组中,例如访问第一个路由就可以用 api/:version/product/by_category
Route::group('api/:version/product',function(){
    Route::get('/by_category','api/:version.Product/getAllInCategory');
    Route::get('/recent','api/:version.Product/getRecent');
    Route::get('/:id','api/:version.Product/getOne',[],['id'=>'\d+']);
});

接口的编写:
1.banner接口:
1.构建验证层

验证层:
主要对用户从前端传入后端接口的值进行检查,是否符合接口接收参数的标准,例如不能为空或必须是整数等
构建基类验证层:
作用:验证传入的参数是否合法      
结果:如果合法返回true  如果不合法就抛出异常
主要方法:goCkeck()
    /**
     * 检测所有客户端发来的参数是否符合验证类规则
     * 基类定义了很多自定义验证方法
     * 这些自定义验证方法其实，也可以直接调用
     * @throws ParameterException
     * @return true
     */
    public function goCheck()
    {
        //1.获取http传入的参数
        //2.对这些参数做校验
//3.初始化
$request = Request::instance();
//4.获取传递的参数
        $param = $request->param();
//5.数据进行验证,验证的规则引用不在这个基类中,而是不同的验证器自定义引用哪些规则
        $result = $this->check($param);
        if (!$result) {
            $e = new ParameterException([
                'msg' => $this->error
            ]);
            throw $e;
        } else {
            return true;
        }
    }
构建验证层时都会先创建一个基类验证器而基类验证器继承TP5框架的validate验证类,用来接收HTTP的传参并且进行校验,并且可以避免正则的复杂性,使用验证层就可以检验传入的参数是否符合格式,例如:手机号
所有的验证器继承基类验证器,并且基类验证器还可以编写多种自定义的验证器,例如:不能为空,调用到各种验证器中,

//必须是整数的判断
    protected function isPositiveInteger($value, $rule = '', $data = '', $field = '')
    {
        //$data=传过来的值
        //$field=验证的名字为id(在上一句)
        //$value=传过来参数的值
        $a = is_numeric($value) && is_int($value + 0) && ($value + 0) > 0;
        if ($a) {
            return true;
        } else {
            return false;
//            return $field.'必须是整数';
        }
    }

    //没有使用TP的正则验证，集中在一处方便以后修改
    //不推荐使用正则，因为复用性太差
    //手机号的验证规则
//手机号的验证
    protected function isMobile($value)
    {
        $rule = '^1(3|4|5|7|8)[0-9]\d{8}$^';
        $result = preg_match($rule, $value);
        if ($result) {
            return true;
        } else {
            return false;
        }
    }
//不能为空的验证
    protected function isNotEmpty($value, $rule = '', $data = '', $field = '')
    {
        if (empty($value)) {
            return false;
        } else {
            return true;
        }
    }
//不能输入非法字段的判断
    public function getDataByRule($arrays)
    {
        if (array_key_exists('user_id', $arrays) | array_key_exists('uid', $arrays)) {
            // 不允许包含user_id或者uid，防止恶意覆盖user_id外键
            throw new ParameterException([
                'msg' => '参数中包含有非法的参数名user_id或者uid'
            ]);
        }
        $newArray = [];
        foreach ($this->rule as $key => $value) {
            $newArray[$key] = $arrays[$key];
        }
        return $newArray;
    }
构建验证器:
作用:进行对接口接收数据的验证,
用法:使用固定变量$rule对值与规则进行对应, 使用$message自定义返回的错误信息
//继承了基类验证器,
class Count extends BaseValidate
{
protected $rule=[
  'id'=>'require|isPositiveInteger',
//	 要验证的字段    验证的规则1(|代表并且)|验证规则2
];
//以下定义的是返回的错误信息
protected $message=[
    'id'=>'必须是正整数'
];
}
//也可以直接调用基类中的自定义验证方法,直接进行验证
if(!$this->isPositiveInteger($id)){
    return false;
}










