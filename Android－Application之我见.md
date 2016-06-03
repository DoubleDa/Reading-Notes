# Android Application之我见

## Application

* 继承 ：ContextWrapper
* 实现 ：ComponentCallbacks2
* 全局变量 ：
			
		mComponentCallbacks：存放ComponentCallbacks对象的List集合
		mActivityLifecycleCallbacks：存放ActivityLifecycleCallbacks对象的List集合
		mAssistCallbacks：存放OnProvideAssistDataListener对象的List集合
		mLoadedApk：LoadedApk对象
* 方法 ：

		Application()：构造方法
		onCreate()：当application启动的时候，在activity、service、receiver对象、content providers被创建之前调用
		onTerminate()：这个方法为模拟器环境提供，在一个生产环境的Android设备不会调用此方法
		onConfigurationChanged(Configuration newConfig)：当设备的所有配置信息发生变化时，将会被调用，包括：用户自定义（locale和scaling）、设备配置（input modes、screen size和screen orientation）
		onLowMemory()：当整个系统在低内存条件下运行时，或者正在运行的进程需要调整它们的内存使用，
		onTrimMemory(int level)：当操作系统已经决定适时为这个进程释放无用的内存的时候调用
		registerComponentCallbacks(ComponentCallbacks callback)：向mComponentCallbacks集合添加ComponentCallbacks对象
		unregisterComponentCallbacks(ComponentCallbacks callback)：从mComponentCallbacks集合移除ComponentCallbacks对象
		registerActivityLifecycleCallbacks(ActivityLifecycleCallbacks callback)：向mActivityLifecycleCallbacks集合添加ActivityLifecycleCallbacks对象
		unregisterActivityLifecycleCallbacks(ActivityLifecycleCallbacks callback)：从mActivityLifecycleCallbacks集合移除ActivityLifecycleCallbacks对象
		registerOnProvideAssistDataListener(OnProvideAssistDataListener callback)：向mAssistCallbacks集合添加OnProvideAssistDataListener对象
		unregisterOnProvideAssistDataListener(OnProvideAssistDataListener callback)：从mAssistCallbacks集合移除OnProvideAssistDataListener对象
		---Internal API---
		attach(Context context)：将context对象绑定到ContextWrapper，获取LoadedApk对象
		dispatchActivityCreated(Activity activity, Bundle savedInstanceState)：分派onActivityCreated状态
		dispatchActivityStarted(Activity activity)：分派onActivityStarted状态
		dispatchActivityResumed(Activity activity)：分派onActivityResumed状态
		dispatchActivityPaused(Activity activity)：分派onActivityPaused状态
		dispatchActivityStopped(Activity activity)：分派onActivityStopped状态
		dispatchActivitySaveInstanceState(Activity activity, Bundle outState)：分派onActivitySaveInstanceState状态
		dispatchActivityDestroyed(Activity activity)：分派onActivityDestroyed状态
		collectComponentCallbacks()：将mComponentCallbacks集合转换为数组
		collectActivityLifecycleCallbacks()：将mActivityLifecycleCallbacks集合转换为数组
		dispatchOnProvideAssistData(Activity activity, Bundle data)：当用户正在请求一个Assist_Action去创建全局的Intent为当前application的context时调用
		
* 接口 ：

		ActivityLifecycleCallbacks
		|onActivityCreated(Activity activity, Bundle savedInstanceState)
		|onActivityStarted(Activity activity)
		|onActivityResumed(Activity activity)
		|onActivityPaused(Activity activity)
		|onActivityStopped(Activity activity)
		|onActivitySaveInstanceState(Activity activity, Bundle outState)
		|onActivityDestroyed(Activity activity)
		OnProvideAssistDataListener
		|onProvideAssistData(Activity activity, Bundle data)
		
* 其他 ：

		｜获取Configuration信息：Configuration config = getResources().getConfiguration();


* 调用关系

![](https://raw.githubusercontent.com/DoubleDa/Reading-Notes/master/Application%E7%B1%BB%E8%B0%83%E7%94%A8%E5%85%B3%E7%B3%BB.jpg)

* 总结


