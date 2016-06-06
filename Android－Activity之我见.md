# Android－Activity之我见

## 模板

* 继承 ：

		ContextThemeWrapper

* 实现 ：

		LayoutInflater.Factory2
		Window.Callback
		KeyEvent.Callback
		OnCreateContextMenuListener
		ComponentCallbacks2
		Window.OnWindowDismissedCallback

* 全局变量 ：

		只列举出重要的！
		SparseArray<ManagedDialog> mManagedDialogs：用于存储ManagedDialog的集合
		Instrumentation mInstrumentation：
		IBinder mToken：
		Application mApplication：
		Intent mIntent：
		ComponentName mComponent
		ActivityInfo mActivityInfo
		ActivityThread mMainThread
		Activity mParent
		Configuration mCurrentConfig
		SearchManager mSearchManager
		MenuInflater mMenuInflater
		NonConfigurationInstances mLastNonConfigurationInstances
		Window mWindow
		WindowManager mWindowManager
		View mDecor
		ActionBar mActionBar
		VoiceInteractor mVoiceInteractor
		Handler mHandler
		FragmentController mFragments
		ArrayList<ManagedCursor> mManagedCursors
		Intent mResultData
		TranslucentConversionListener mTranslucentCallback
		SearchEvent mSearchEvent
		SpannableStringBuilder mDefaultKeySsb
		Thread mUiThread
		ActivityTransitionState mActivityTransitionState
		SharedElementCallback mEnterTransitionListener
		SharedElementCallback mExitTransitionListener
		
		
		
		

* 内部类

		ManagedDialog
		|Dialog mDialog
		|Bundle mArgs
		
		NonConfigurationInstances
		|Object activity
		|HashMap<String, Object> children
		|List<Fragment> fragments
		|ArrayMap<String, LoaderManager> loaders
		|VoiceInteractor voiceInteractor
		
		ManagedCursor
		|Cursor mCursor


* 方法 ：

		public Intent getIntent()
		setIntent(Intent newIntent)
		Application getApplication()
		boolean isChild()
		Activity getParent()
		WindowManager getWindowManager()
		Window getWindow()
		LoaderManager getLoaderManager()
		View getCurrentFocus()
		void onCreate(@Nullable Bundle savedInstanceState)
		void onCreate(@Nullable Bundle savedInstanceState,@Nullable PersistableBundle persistentState)
		void performRestoreInstanceState(Bundle savedInstanceState) 
		void performRestoreInstanceState(Bundle savedInstanceState,PersistableBundle persistentState)
		void onRestoreInstanceState(Bundle savedInstanceState)
		void onRestoreInstanceState(Bundle savedInstanceState,PersistableBundle persistentState)
		void restoreManagedDialogs(Bundle savedInstanceState)
		Dialog createDialog(Integer dialogId, Bundle state, Bundle args)
		String savedDialogKeyFor(int key)
		String savedDialogArgsKeyFor(int key)
		void onPostCreate(@Nullable Bundle savedInstanceState)
		void onPostCreate(@Nullable Bundle savedInstanceState,@Nullable PersistableBundle persistentState)
		void onStart()
		void onRestart()
		void onStateNotSaved()
		void onResume()
		void onPostResume()
		boolean isVoiceInteraction()
		boolean isVoiceInteractionRoot()
		//TODO 1248

* 接口 ：




* 其他 ：


* 调用关系：


* 总结


















