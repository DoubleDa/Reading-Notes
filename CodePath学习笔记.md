# CodePath学习笔记

## Creating Custom Listeners

Type           | Called By           | Description
------------   | -------------       | ------------
Intents        | Activity            | Intents should be created and executed within activities
Networking     | Activity, Fragment  | Networking code should invoked in an activity or fragment
FragmentManager| Activity            | Fragment changes should be invoked by an activity
Persistence    | Activity, Fragment  | Writing to disk should be invoked by activity or fragment

There are four steps to using a custom listener to manage callbacks in your code

* Define an interface
* Setup a listener member variable
* Owner passes in a listener
* Trigger events on the defined listener

There are several different ways to pass a listener callback into the child object:

* Passing via Method

		// Inside the parent object
		childObject.setCustomObjectListener(new MyCustomObjectListener() {
    		@Override
    		public void onObjectReady(String title) {
        		// Code to handle object ready
    		}
		});

	which is defined in the child object as follows:
	
		// Inside the child object
		private MyCustomObjectListener listener;

		// Assign the listener implementing events interface that will receive the events
		public void setCustomObjectListener(MyCustomObjectListener listener) {
    		this.listener = listener;
		}

* Passing via Constructor

If the callback is critical to the object's function, we can pass the callback directly into the constructor of the child object as an argument:

		// Inside the child object
		private MyCustomObjectListener listener;

		// Passing in the listener directly into the constructor
		public MyCustomObject(MyCustomObjectListener listener) {
    		this.listener = listener; 
		}
		
and then when we can create the child object from the parent we can do the following:

		// Inside the parent object
		MyCustomObject object = new MyCustomObject(new MyCustomObjectListener() {
    		@Override
    		public void onObjectReady(String title) {
        		// Code to handle object ready
    		});
		});
		
* Pass via Lifecycle Event

The third case is most common with fragments or other android components that need to communicate upward to a parent. 

		public class MyListFragment extends Fragment {
  				//Member variable storing the listener
  				private MyCustomObjectListener listener;
  				
  				// Store the listener that will have events fired once the fragment is attached
  				@Override
 				 public void onAttach(Context context) {
    			super.onAttach(context);
    			if (context instanceof MyCustomObjectListener) {
        			listener = (MyCustomObjectListener) context;
    			} else {
        		throw new ClassCastException(context.toString()
            		+ " must implement MyListFragment.MyCustomObjectListener");
    			}
  			}
		}