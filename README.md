# milkteamanage
Java：185 基于SSM的奶茶店管理系统
> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

# 项目介绍

奶茶店管理系统的用户分管理员和用户两个角色的权限子模块。

管理员所能使用的功能主要有：主页、个人中心、用户管理、奶茶分类管理、奶茶信息管理、系统管理、订单管理等。

用户可以实现主页、个人中心、我的收藏管理、订单管理等。

前台首页可以实现奶茶信息、新闻资讯、我的、跳转到后台、购物车等。

# 环境要求

1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA;

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS;

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目

6.数据库：MySql5.7/8.0等版本均可；

# 技术栈

运行环境：jdk8 + tomcat9 + mysql5.7 + windows10

服务端技术：Java、Spring、SpringMVC、Mybatis，SSM

前端：jsp

# 使用说明

1.使用Navicati或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件；

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目；

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq

源码地址：[http://www.codegym.top](http://www.codegym.top/)



# 运行截图

## 功能模块截图

![image20241217000708373](https://i-blog.csdnimg.cn/img_convert/0c04ba4674c933848fcdb0da38623f81.png)

![image20241217000734813](https://i-blog.csdnimg.cn/img_convert/43f18c84986812a811a70b7ee88f0866.png)

### 项目截图

前台

![ssm140基于java的奶茶店管理系统的设计与实现jsp0](https://i-blog.csdnimg.cn/img_convert/06ca42b54dd44f1ba23004b2bafc731f.png)

![ssm140基于java的奶茶店管理系统的设计与实现jsp1](https://i-blog.csdnimg.cn/img_convert/1c628cf1c399bdda7f88c1716aa7289b.png)

![ssm140基于java的奶茶店管理系统的设计与实现jsp2](https://i-blog.csdnimg.cn/img_convert/e93fd515c023e70698b83715bf26b656.png)

![ssm140基于java的奶茶店管理系统的设计与实现jsp3](https://i-blog.csdnimg.cn/img_convert/bb13cc0ddf6770727a0a935627b2ee45.png)

![ssm140基于java的奶茶店管理系统的设计与实现jsp4](https://i-blog.csdnimg.cn/img_convert/eacd510f963aaadea30953308d2f2d03.png)

后台

![ssm140基于java的奶茶店管理系统的设计与实现jsp6](https://i-blog.csdnimg.cn/img_convert/e933d15355f4c9ffb17c58aa5274ffb6.png)

![ssm140基于java的奶茶店管理系统的设计与实现jsp7](https://i-blog.csdnimg.cn/img_convert/4fd1ee172244738d77933970c7560472.png)

![ssm140基于java的奶茶店管理系统的设计与实现jsp8](https://i-blog.csdnimg.cn/img_convert/138d404472dd5db27112558fe6fbeae4.png)
### 代码

```
    @RequestMapping("/page")
    public R page(@RequestParam Map<String, Object> params,StoreupEntity storeup, HttpServletRequest request){
    	if(!request.getSession().getAttribute("role").toString().equals("管理员")) {
    		storeup.setUserid((Long)request.getSession().getAttribute("userId"));
    	}

        EntityWrapper<StoreupEntity> ew = new EntityWrapper<StoreupEntity>();
		PageUtils page = storeupService.queryPage(params, MPUtil.sort(MPUtil.between(MPUtil.likeOrEq(ew, storeup), params), params));
        return R.ok().put("data", page);
    }
```

