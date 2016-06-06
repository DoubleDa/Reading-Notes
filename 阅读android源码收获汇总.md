# 阅读Android源码收益汇总

* 使用synchronized处理集合

		private Object[] collectComponentCallbacks() {
        	Object[] callbacks = null;
        	synchronized (mComponentCallbacks) {
            	if (mComponentCallbacks.size() > 0) {
                	callbacks = mComponentCallbacks.toArray();
            	}
        	}
        	return callbacks;
    	}
	说明：
	
	｜集合的正确使用方法，集合有可能被多个对象访问，所以使用synchronized关键字标志，确保数据操作的同步；
	
	｜集合mComponentCallbacks的size()方法使用场景：返回int的size；
	
	｜集合mComponentCallbacks的!=null使用场景：对象是不是为null；
	 
	｜集合mComponentCallbacks的isEmpty()方法使用场景：通过判断“size == 0”返回boolean值；

* ArrayList集合的创建时机

		//代码片段1
		private ArrayList<ComponentCallbacks> mComponentCallbacks =
            		new ArrayList<ComponentCallbacks>();
        //代码片段2
        private ArrayList<OnProvideAssistDataListener> mAssistCallbacks = null;
        //代码片段3
        synchronized (this) {
            if (mAssistCallbacks == null) {
                mAssistCallbacks = new ArrayList<OnProvideAssistDataListener>();
            }
            mAssistCallbacks.add(callback);
        }
	说明：
	
	｜全局使用到的集合，使用代码片段1
	
	｜只有在需要使用时创建的，使用代码片段2和代码片段3
	
* SparseArray的使用

		private SparseArray<ManagedDialog> mManagedDialogs;
		
		if (mManagedDialogs != null) {
            		final int numDialogs = mManagedDialogs.size();
            		for (int i = 0; i < numDialogs; i++) {
                		final ManagedDialog md = mManagedDialogs.valueAt(i);
                		if (md.mDialog.isShowing()) {
                    		md.mDialog.dismiss();
                		}
            		}
            		mManagedDialogs = null;
        		}



	