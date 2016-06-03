# Android－ContextWrapper之我见

## ContextWrapper

* 继承 ：Context

* 实现 ：无

* 全局变量 ：

		mBase：Context对象


* 方法 ：

		ContextWrapper(Context base)：ContextWrapper构造方法
		attachBaseContext(Context base)：为ContextWrapper设置基本的context，所有的访问将被委托到基本的Context。如果一个基本的Context已经被设定，将会抛出IllegalStateException。
		getBaseContext：
		getAssets：
		getResources：
		getPackageManager：
		getContentResolver：
		getMainLooper：
		getApplicationContext：
		setTheme：
		getThemeResId：
		getTheme：
		getClassLoader：
		getPackageName：
		getBasePackageName：
		getOpPackageName：
		getApplicationInfo：
		getPackageResourcePath：
		getPackageCodePath：
		getSharedPrefsFile(String name)：
		getSharedPreferences(String name, int mode)：
		openFileInput(String name)：
		openFileOutput(String name, int mode)：
		deleteFile(String name)：
		getFileStreamPath(String name)：
		fileList()：
		getFilesDir()：
		getNoBackupFilesDir()：
		getExternalFilesDir(String type)：
		getExternalFilesDirs(String type)：
		getObbDir()：
		getObbDirs()：
		getCacheDir()：
		getCodeCacheDir()：
		getExternalCacheDir()：
		getExternalCacheDirs()：
		getExternalMediaDirs()
		getDir(String name, int mode)
		openOrCreateDatabase(String name, int mode, CursorFactory factory)
		openOrCreateDatabase(String name, int mode, CursorFactory factory,
            DatabaseErrorHandler errorHandler)
        deleteDatabase(String name)
        getDatabasePath(String name)
        databaseList()
        getWallpaper()
        peekWallpaper()
        getWallpaperDesiredMinimumWidth()
        getWallpaperDesiredMinimumHeight()
        setWallpaper(Bitmap bitmap)
        setWallpaper(InputStream data)
        clearWallpaper()
        startActivity(Intent intent)
        startActivityAsUser(Intent intent, UserHandle user)
        startActivityForResult(
            String who, Intent intent, int requestCode, Bundle options)
        canStartActivityForResult()
        startActivity(Intent intent, Bundle options)
        startActivityAsUser(Intent intent, Bundle options, UserHandle user)
        startActivities(Intent[] intents)
        startActivities(Intent[] intents, Bundle options)
        startActivitiesAsUser(Intent[] intents, Bundle options, UserHandle userHandle)
        startIntentSender(IntentSender intent,
            Intent fillInIntent, int flagsMask, int flagsValues, int extraFlags)
        startIntentSender(IntentSender intent,
            Intent fillInIntent, int flagsMask, int flagsValues, int extraFlags,
            Bundle options)
        sendBroadcast(Intent intent)
        sendBroadcast(Intent intent, String receiverPermission)
        sendBroadcastMultiplePermissions(Intent intent, String[] receiverPermissions)
        sendBroadcast(Intent intent, String receiverPermission, Bundle options)
        sendBroadcast(Intent intent, String receiverPermission, int appOp)
        sendOrderedBroadcast(Intent intent,String receiverPermission)
        sendOrderedBroadcast(Intent intent, String receiverPermission, BroadcastReceiver 		resultReceiver,Handler scheduler, int initialCode, String initialData,Bundle 		initialExtras)
        sendOrderedBroadcast(Intent intent, String receiverPermission, Bundle options, 		BroadcastReceiver resultReceiver,Handler scheduler, int initialCode, String 		initialData,Bundle initialExtras)
        sendOrderedBroadcast(
        Intent intent, String receiverPermission, int appOp, BroadcastReceiver resultReceiver,
        Handler scheduler, int initialCode, String initialData,
        Bundle initialExtras)
        sendBroadcastAsUser(Intent intent, UserHandle user)
        sendBroadcastAsUser(Intent intent, UserHandle user,String receiverPermission)
        sendBroadcastAsUser(Intent intent, UserHandle user,
            String receiverPermission, int appOp)
        ……
        
* 接口 ：
无

* 其他 ：

* 各类调用关系


![](https://raw.githubusercontent.com/DoubleDa/Reading-Notes/master/ContextWrapper%E7%B1%BB%E8%B0%83%E7%94%A8%E5%85%B3%E7%B3%BB.jpg)

* 总结

	在ContextWrapper进行的工作总结：
	
		代理实现Context，可以简单的委托它所有的访问到其他的Context，子类可以改变动作不用改变原始的Context。
	
	
	| 名称           		 | 具体内容       | 
	| :--------------------:|:-------------:|
	| 构造ContextWrapper对象  | 将基本的Context设定到ContextWrapper，或者通过setBaseContext |  
	| 获取基本Context属性     | 通过mBase可以获取的属性有：Assets、Resources、PackageManager、ContentResolver、MainLooper、ApplicationContext、ThemeResId、Theme、ClassLoader、PackageName、BasePackageName、OpPackageName、ApplicationInfo、PackageResourcePath、PackageCodePath、SharedPrefsFile、SharedPreferences、FileStreamPath、FilesDir、NoBackupFilesDir、ExternalFilesDir、ExternalFilesDirs、ObbDir、ObbDirs、CacheDir、CodeCacheDir、ExternalCacheDir、ExternalCacheDirs、ExternalMediaDirs、Dir、DatabasePath、Wallpaper、WallpaperDesiredMinimumWidth、WallpaperDesiredMinimumHeight、SystemService、SystemServiceName、UserId、DisplayAdjustments |  
	|为Context设置属性 | Theme、Wallpaper  |
	| 为Context删除操作	| File、Database|
	| 在Context进行文件操作	| fileList|
	| 在Context进行数据库操作	|	openOrCreateDatabase、databaseList、|
	|在Context进行壁纸操作	|	getWallpaper、peekWallpaper、getWallpaperDesiredMinimumWidth、getWallpaperDesiredMinimumHeight、setWallpaper、clearWallpaper|
	|在Context中对Activity进行操作	|	startActivity、startActivityAsUser、startActivityForResult、canStartActivityForResult、startActivities、startActivitiesAsUser、startIntentSender|
	|在Context中对Broadcast进行操作|	sendBroadcast、sendBroadcastMultiplePermissions、sendOrderedBroadcast、sendBroadcastAsUser、sendOrderedBroadcastAsUser、sendStickyBroadcast、sendStickyOrderedBroadcast、removeStickyBroadcast、sendStickyBroadcastAsUser、sendStickyOrderedBroadcastAsUser、removeStickyBroadcastAsUser、registerReceiver、registerReceiverAsUser、unregisterReceiver|
	|	在Context中对Service进行操作|startService、stopService、startServiceAsUser、stopServiceAsUser、bindService、bindServiceAsUser、unbindService	|
	|在Context进行测试操作	|	startInstrumentation|
	|在Context进行权限操作	| checkPermission、checkCallingPermission、checkCallingOrSelfPermission、checkSelfPermission、enforcePermission、enforceCallingPermission、enforceCallingOrSelfPermission、grantUriPermission、revokeUriPermission、checkUriPermission、checkCallingUriPermission、checkCallingOrSelfUriPermission、enforceUriPermission、enforceCallingUriPermission、enforceCallingOrSelfUriPermission	|
	|在Context中创建其他的Context	|	createPackageContext、createPackageContextAsUser、createApplicationContext、createConfigurationContext、createDisplayContext|
	|在Context中判断Context是否受约束|isRestricted	|








