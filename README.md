# -----
activity、fragment
singleTop模式

singleTask模式

singleInstance模式

三种启动模式共同之处：（singleTop、singleTask、singleInstance）
	1、第一次启动时候调用：
onCreate
onStart
onResume
	
	2、退出程序
onPause
onStop
onDestroy

	3、跳转第二页面、点击手机home键、放回键
onPause
onStop

	4、第二个页面返回到之前的页面
onRestart
onStart
onResume

	5、自己给自己跳转不管跳几次，返回都是一次返回。
onPause
onResume


2016/11/29
今天的任务Fragment
Activity --- Fragment(管理)
Activity --- Fragment(传递参数)
Fragment的生命周期
fragment（Activity与Fragment生命周期的关系）
Freament(自定义布局加载)

做项目用到启动模式
登陆SingleInstance
主页standard
购车singleTask

收藏流程
通过id收藏。，状态一般0、1表示

Freament(自定义布局加载)

	1、在xml 中，定义 fragment ，可以看到 可以通过name反射，找到fragment,就将自己定义Fragment 中的视图View加载。
	2、还有注意一点就是，fragment ,必须要给他个id，不然的话就不显示fragment内容
Activity --- Fragment(管理)

动态加载:
 //创建Fragment对象
 Fragment fragment1 = new FragmentA();
 //获取Fragment的容器
 FragmentManager manager =getSupportFragmentManager();
 // 获取事务对象 FragmentTransaction，通过容器 ，开启事物
 FragmentTransaction transaction = manager.beginTransaction();
 //事物添加（fragment的id，fragment的对象，名称）remove、replace、show、hide
 transaction.add(R.id.fl, fragment1, "第一页面");
 //提交事物
 transaction.commit();


Activity --- Fragment(传递参数)
使用Bundle
1、 在Activity传值
	1）、创建Bundle对象
	2）、bubdle.put数据类型（键，值）
	3）、fragment. setArguments
2、Fragment得到值
    1)、获取fragment. getArguments
	2）、bubdle.getString(获取key值)

Fragment的生命周期（Activity对Fragment比图）
Activity	Fragment


onCreate	onAttach
	onCreate
	onCreateView
	onActivityCreated
onStart	onStart
onResume	onResume
onPause	onPause
onStop	onStop

onDestroy	onDestroyView
	onDestroy
	onDetach


Fragment与Activity的生命周期调用的方法

1、第一次启动调用的方法：（fragment）
onAttach
onCreate
onCreateView
onActivityCreated
onStart
onResume

2、点击手机home键，锁屏（Activity、fragment）

共同点: onPause、onStop
启动循序：
FragmentA: ----->onPause
MainActivity: ----->onPause
FragmentA: ----->onStop
MainActivity: ----->onStop

3、解锁，反回（Activity、fragment）

共同点:onStart、onResume
不同点: Activity多了onRestart
启动循序：
MainActivity: ----->onRestart
FragmentA: ----->onStart
MainActivity: ----->onStart
MainActivity: ----->onResume
FragmentA: ----->onResume


4、退出程序（Activity、fragment）

共同点: onPause、onStop、onDestroy
不同点: fragment多了onDestroyView、onDetach
启动循序：
FragmentA: ----->onPause
MainActivity: ----->onPause
FragmentA: ----->onStop
MainActivity: ----->onStop
FragmentA: ----->onDestroyView
FragmentA: ----->onDestroy
FragmentA: ----->onDetach
MainActivity: ----->onDestroy


