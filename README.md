<h2 style="margin-bottom: 0;" align="center">Android Interview Essentials</h2>
<h4 style="margin-top: 0;" align="center">Language Basics, Architecture In-depth, Android Vitals, Performance, Memory Optimizations and More</h4>
<p align="center">
	<a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-blue.svg"/></a>
	<a href="https://github.com/SaadAAkash/Native-Android-Interview-Basics"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg"/></a>
	<a href="https://github.com/SaadAAkash/Kotlin-Android-Interview-Basics/commits/master"><img src="https://img.shields.io/badge/Maintained%3F-yes-green.svg"/></a>
	<a href="https://github.com/SaadAAkash/Kotlin-Android-Interview-Basics/tree/master#license"><img src="https://badges.frapsoft.com/os/v1/open-source.svg?v=103"/></a>
	<a href="https://saad.ninja"><img src="https://img.shields.io/badge/Made%20with-Love-1f425f.svg"/></a>
	<br> <br>
	
<a href="https://undraw.co/" target="_blank">
         <img src="https://github.com/SaadAAkash/Kotlin-Android-Interview-Basics/blob/master/resources/banner.jpg" alt="Native Android Interview Basics" style="width:200;height:200">
</a>


## Contents

| 1 | 2 | 3 | 4 | 5 | 6 |
| -------- | --------- | --------- | --------- | --------- | --------- |
| [Android Basics](README.md#android-basics) | [Android Specifics: Native](#android-specifics-native) | [Android Specifics: Cross-Platform](#android-specifics-cross-platform) | [Android Intermediate](#android-intermediate) | [Android Advanced](#android-advanced) | [Resources & Learning Guides](#interview-learning-guides) |

# Android Basics

<details>
<summary><strong>What are the core 4 app components? What elements/tags do we use to declare them in the Manifest file?</strong></summary>
There are four different types of app components:

* Activities
* Services
* Broadcast receivers
* Content providers

To declare all app components, we use the following elements:

* `<activity>` elements for activities.
* `<service>` elements for services.
* `<receiver>` elements for broadcast receivers.
* `<provider>`elements for content providers.
</details>

<details>
<summary><strong>What's Context?</strong></summary>
Context is the Interface to global information about an application environment
</details>

<details>
<summary><strong>What's an Activity?</strong></summary>
An Activity is an application component that provides a screen, with which users can interact in order to do something
</details>

<details>
<summary><strong>What's a Fragment? What's its relationship with Activity?</strong></summary>
A Fragment represents a behavior or a portion of user interface in an Activity. A fragment has to live inside the activity. Fragments do not need to be declared in the manifest.
</details>

<details>
<summary><strong>What's the use of Fragment?</strong></summary>
Fragments are used for its re-usability. For multi-pane layouts you have to use fragment that you can't achieve with activity. Use fragment only when you’re working with UI components or behavior that you’re going to use across multiple activities
</details>

<details>
<summary><strong>What's a Service?</strong></summary>
A service is a component that runs in the background to perform long-running operations without needing to interact with the user and it works even if application is destroyed
</details>

<details>
<summary><strong>What's an Intent? How many types of intent are in Android? Briefly explain their respective use cases.</strong></summary>

An Intent is a messaging object you can use to request an action from another app component.

Use Cases: Starting an Activity or a Service, Delivering a broadcast. 
* <b>Explicit intents</b> are used to start components in your own application. Use Case: You might start a new activity within your app in response to a user action, or start a service to download a file in the background.
* <b>Implicit intents</b> are most commonly used to communicate with components from other third party applications.  Use Case: If you want to show the user a location on a map, you can use an implicit intent to request that another capable app show a specified location on a map.

</details>

<details>
<summary><strong>What's a PendingIntent? How many types of intent are in Android? Briefly explain their respective use cases.</strong></summary>

A PendingIntent object is a wrapper around an Intent object. The primary purpose of a PendingIntent is to grant permission to a foreign application to use the contained Intent as if it were executed from your app's own process.

Use Cases: 
* Notification: Android system's NotificationManager executes the Intent
* App Widget: Home screen app executes the Intent
* A specified future time: Android system's AlarmManager executes the Intent

</details>

<details>
<summary><strong>What is the functionality of Intent filters? Point out a frequently-used scenario.</strong></summary>

This element is used in the Manifest file to declare the capabilities of an app component (i.e. an Activity) 

Use Case:
When we declare an Activity in the Manifest, we can include intent filters so it can respond to intents from other applications like the following:

```xml
<manifest>
    ...
    <application>
        <activity android:name="com.example.SendEmailActivity">
            <intent-filter>
                <action android:name="android.intent.action.SEND" />
                <data android:type="*/*" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

</details>

<details>
<summary><strong>What are the core components of RecyclerView?</strong></summary>

* RecyclerView.Adapter
* RecyclerView.ViewHolder
* RecyclerView.LayoutManager
* RecyclerView.ItemAnimator

</details>

<details>
<summary><strong>What are the functionalities/use cases of using Guideline & Barries in a ConstraintLayout?</strong></summary>

Link to the resources with graphical explanation:

* [Constrain to a guideline](https://developer.android.com/training/constraint-layout#constrain-to-a-guideline)
* [Constrain to a barrier](https://developer.android.com/training/constraint-layout#constrain-to-a-barrier)

</details>

<details>
<summary><strong>Which method is called only once in a fragment life cycle?</strong></summary>
onAttached()
</details>



# Android Specifics: Native

### Android Specifics: Kotlin

* [Main Reference Guide](https://kotlinlang.org/docs/reference/)
* [From Java to Kotlin](https://github.com/MindorksOpenSource/from-java-to-kotlin)
* [Kotlin Tutorial Series Playlist by Navir Reddy](https://www.youtube.com/playlist?list=PLsyeobzWxl7rooJFZhc3qPLwVROovGCfh)
* Declare a variable as nullable string (var_name?):

  ```
	var a: String = "abc"
	a = null // compilation error
	var b: String? = "abc"
	b = null // no error
	print(b)
  ```
 
* Safe call operator (?.)

  ```
	val a = "Kotlin"
	val b: String? = null
	println(b?.length)
	println(a?.length)

	output:
	null
	6 
   ```
* !! vs ? 

   ```
        +------------+--------------------+---------------------+----------------------+
        | a: String? |           a.length |           a?.length |           a!!.length |
        +------------+--------------------+---------------------+----------------------+
        |      "cat" | Compile time error |                   3 |                    3 |
        |       null | Compile time error |                null | NullPointerException |
        +------------+--------------------+---------------------+----------------------+
   ```
   
   !! is an option for NPE-lovers. ```a!!.length``` will return a non-null value of a.length or throw a NullPointerException if a is null. And ```a?.length``` returns a.length if a is not null, and null otherwise:

   ```
   val a: String? = null
   print(a!!.length) // >>> NPE: trying to get length of null
   ```

   ```
   val a: String? = null
   print(a?.length) // >>> null is printed in the console
   ```
   
* Ternary Operator: **Unlike Java, there is no ternary operator in kotlin. Use if-else instead**

* Bitwise Operator:

   ```
   val andResult  = a and b
   val orResult   = a or b
   val xorResult  = a xor b
   val rightShift = a shr 2
   val leftShift  = a shl 2
   ```

* Elvis Operator: The Smarter Type-Safe If

   ```
   val list = mutableList ?: mutableListOf() 
   ```
	is a shorter form of
   ```
   val list = if (mutableList != null) mutableList else mutableListOf()
   ```
   
   The name,howver, comes from the famous American singer Elvis Presley. His hairstyle resembles a Question Mark [Ref](https://stackoverflow.com/questions/48253107/what-does-do-in-kotlin/48304523#48304523)
   
   ![alt text](https://i.stack.imgur.com/bVG64.png "Elvis Operator")

* when, if
   ```
	return if (x) foo() else bar()
	return when(x) {
	    0 -> "zero"
	    else -> "nonzero"
	}
    ```
    
     The above is preferable to:
     ```
	if (x)
	    return foo()
	else
	    return bar()

	when(x) {
	    0 -> return "zero"
	    else -> return "nonzero"
	}
     ```
     
* Functions

  ```
	fun double(x: Int): Int {
	    return 2 * x
	} 
	//SYNTAX: 
	fun funName( param : paramType ) : returnType
	{

	}
   ```

* Visibility Modifiers (public, protected, internal, private): public is used by default, means it will be visible everywhere.	If a declaration's private, it will only be visible inside the file containing the declaration.	If it's internal, it is visible everywhere in the same **module** (a module is a set of Kotlin files compiled together: IntelliJ IDEA, Gradle source set etc) and if protected, it's not available for top-level declarations.

  ```
	 class EventViewModel internal constructor(
	)
	//internal makes class available to public, but constructor only to inside module
  ```

* Always declare local variables and properties as ```val``` rather than ```var``` if they are not modified (not variable) after initialization
* Prefer using immutable (whose state cannot be modified after it is created) data to mutable.
* Out Initialization code can be placed in initializer blocks, which are prefixed with the ```init``` keyword:

  ```
  class InitOrderDemo(name: String) {
	    val firstProperty = "First property: $name".also(::println)  //inits a val & also, prints the name
	    
	    init {
	        println("First initializer block that prints ${name}")
	        println("Second initializer block that prints ${name.length}")
	    }
	}
  ```
  
* Calling High Order Functions
  ``` 
	fun main() {
	//both of the ways are correct!
	    test( { println(it) } ) 
	    test(::println)
	}

	fun test(block: (String) -> Unit ) {
	    block("okay")
	}
  ```
* A sample input-output problem solving in kotlin example

  ```
  fun solve (clawPos: Int, boxes: Array<Int>, boxInClaw: Boolean): String {
  	return "okay"
  }
  fun main(args : Array<String>) {
    val input = Scanner(System.`in`)
    while (true) {
        val clawPos = input.nextInt()  //4
        val boxInClaw = input.nextInt() != 0 //0
        val stacks = input.nextInt()  //5
        val boxes = Array(stacks) { input.nextInt() } //1 4 1 2 3
        val outStream = System.out
        System.setOut(System.err)
        val action: String = solve(clawPos, boxes, boxInClaw)
        System.setOut(outStream)
        println(action)
    }
  }
  ```
* @Volatile before a field means that writes to this field are immediately made visible to other threads.
* Suppress Warnings: In Kotlin, there's no way to check the generic parameters at runtime in general case (like just checking the items of a ```List<T>``` or here in this ViewModelFactory, ```modelClass: Class<T>``` which is only a special case), so casting a generic type to another with different generic parameters will raise a warning, which needs to be suppressed

  ```
  @Suppress("UNCHECKED_CAST")
	 override fun <T : ViewModel?> create(modelClass: Class<T>) = EventViewModel(eventRepository, lifecycleOwner) as T
  ```
* Companion Objects: if you declare a companion object inside your class, you'll be able to call its members with the same syntax as calling static methods in Java/C#, using only the class name as a qualifier.

  ```
  companion object {
      @Volatile private var instance: EventRepository? = null

      fun getInstance(eventDao:EventDao) =
          instance ?: synchronized(this) {
              instance ?: EventRepository(eventDao).also { instance = it }
          }
   }
   ```

* Let’s say that we have nullable nameTextView. The following code will give us NPE if it is null:
	```
	nameTextView.setEnabled(true)
	```
  But Kotlin, actually, is good and it will not allow us to even do such a thing. It will force us to use ? or !! operator. If we use ? operator:
	```
	nameTextView?.setEnabled(true)
	```
  the line will be proceeded only if nameTextView is not a null. In another case, if we use !! operator:
	```
	nameTextView!!.setEnabled(true)
	```
  it will give us NPE if nameTextView is a null. It's just for adventurers!!!!
  
* Use Let:
	```
	sheetBehavior = BottomSheetBehavior.from(layoutMapBottomSheet!!)
	```
	Use let & use the it rather than the using !! & waiting to get an NPE
	```
	layoutMapBottomSheet?.let {
            sheetBehavior = BottomSheetBehavior.from(it)  //here, "it" is "layoutMapBottomSheet"
        }
	```

### Android Specifics: Java

<details>
<summary><strong>What's the access modifier of a method that no child class can extend/access/override?</strong></summary>
final
</details>

<details>
<summary><strong>How to make a member variable not to be serialized inside a Serialized object?</strong></summary>
Using Java keyword transient.
</details>

<details>
<summary><strong>What's the Parent class of Error & Exception?</strong></summary>
Throwable
</details>

<details>
<summary><strong>Are String objects mutable? If so, why is that? Explain shortly.</strong></summary>
No. String objects are immutable. In the String constant pool, a String object is likely to have one or many references. If several references point to same String without even knowing it, it would be bad if one of the references modified that String value. That's why String objects are immutable.
</details>

<details>
<summary><strong>When to use StringBuffer and when to StringBuilder?</strong></summary>
StringBuffer and StringBuilder are similar, but StringBuilder is faster and preferred over StringBuffer for single threaded program. If thread safety is needed, then StringBuffer is used.
</details>

<details>
<summary><strong>How many types of polymorphism is there in Java?</strong></summary>
There are two types of polymorphism in Java: compile-time polymorphism and runtime polymorphism. We can perform polymorphism in java by method overloading and method overriding. If you overload a static method in Java, it is the example of compile time polymorphism. 
</details>

<details>
<summary><strong>How does Thread communicate?</strong></summary>
Threads communicate in 3 ways: ```wait()```, ```notify()```, ```notifyAll()```
</details>

# Android Specifics: Cross-Platform

### Android Specifics: Dart

### Android Specifics: Flutter

### Android Specifics: Flutter Resources

# Android Intermediate

### General Concepts

<details>
<summary><strong>We know that when one activity starts another, they both experience lifecycle transitions. Briefly explain the order of operations that occur when Activity A starts Activity B.</strong></summary>
* Activity A's onPause() method executes.
* Activity B's onCreate(), onStart(), and onResume() methods execute in sequence. (Activity B now has user focus.)
* Then, if Activity A is no longer visible on screen, its onStop() method executes.
</details>

<details>
<summary><strong>What type of stack does Android use for managing tasks?</strong></summary>
Android manages tasks and the back stack, by placing all activities started in succession in the same task and in a "last in, first out" stack
</details>

<details>
<summary><strong>What are the 3 principal intent flags for managing tasks in Activity Back Stack?</strong></summary>

* FLAG_ACTIVITY_NEW_TASK
* FLAG_ACTIVITY_CLEAR_TOP
* FLAG_ACTIVITY_SINGLE_TOP
	
[More explanation](https://developer.android.com/guide/components/activities/tasks-and-back-stack#IntentFlagsForTasks)
</details>

<details>
<summary><strong>On Android 10 or higher, how can an app start activities?</strong></summary>
By displaying notifications. But there are some exceptions and apps running on Android 10 or higher can start activities only when [one or more of these conditions](https://developer.android.com/guide/components/activities/background-starts#exceptions) are met.

</details>

<details>
<summary><strong>How to retrieve NavController in Java and Kotlin?</strong></summary>
You can retrieve a NavController by using one of the following methods:

* Kotlin:
```
Fragment.findNavController()
View.findNavController()
Activity.findNavController(viewId: Int)
```
* Java:
```
NavHostFragment.findNavController(Fragment)
Navigation.findNavController(Activity, @IdRes int viewId)
Navigation.findNavController(View)
```
</details>

<details>
<summary><strong>What are the major components of Room?</strong></summary>
3 major components in Room:
* Database
* Entity
* DAO
</details>

<details>
<summary><strong>What's Scoped Storage in Android 10?</strong></summary>
Apps that use scoped storage have access only to their app directory on external storage plus any media the app created.
More details on this [article](https://www.raywenderlich.com/9577211-scoped-storage-in-android-10-getting-started).
</details>

<details>
<summary><strong>What's the improved data storage solution aimed at replacing SharedPreferences?</strong></summary>
Jetpack  DataStore
</details>

<details>
<summary><strong>When to use MutableLiveData & when to use LiveData? Explain a scenario.</strong></summary>
when you don't want your data to be modified use LiveData If you want to modify your data later use MutableLiveData. 
A scenario of fetching data from an API needs a MutableLiveData where there are changes in data. This fetched data then can be stored in a LiveData if there's no requirement to change it afterwards & just use cases of using it for the view purposes.
</details>

<details>
<summary><strong>When do we need a Parcelables and when a Bundle? Explain a scenario.</strong></summary>
when you don't want your data to be modified use LiveData If you want to modify your data later use MutableLiveData. 
A scenario of fetching data from an API needs a MutableLiveData where there are changes in data. This fetched data then can be stored in a LiveData if there's no requirement to change it afterwards & just use cases of using it for the view purposes.
</details>

### Common App Architectures: MVVM

* ViewModel: While you're rotating the screen orientation or perform any changes in configruation, data may be lost (i.e. while filling up a google form activity & changing the rotation on device)
* ViewModel prevents memory leak, by hodling the data of UI.
* While fetching data from some API, some data can come after the initilization of the activity & its view.
* LiveData, an observer class, detects & changes the data in the UI if there's any change. LiveData is a data wrapper class, which is observable within a Lifecycle of Activity, Fragment, meaning that the observers are going to be notified only when the Activity or Fragment it’s active.
* When data is ready on the VM side, it’s time to wrap it in LiveData object using MutableLiveData
* Unlike the Presenter, VM is automatically retained on configuration changes with the help of ViewModelProviders, and finished only when Activity finishes or Fragment gets detached without saving state.
* If A is a LiveData instance and B is observing it, anytime A’s data changes, B is notified about this change and gets the latest value of A’s data.
* **Lifecycle awareness** : This means that a LiveData will only update observers (such as Activities, fragments or services) which are in an active lifecycle state and thus, avoiding NPE
* There is no reference to the View from a ViewModel so the communication between them must happen via a subscription. Hence, ViewModels expose events like openTaskEvent and views subscribe to them. 

* Process:

1.  Import androidx lifecycle components & initialize the viewmodel in an Activity:
	``` 
	import androidx.lifecycle.ViewModelProvider
	////
	lateinit var paymentViewModel : PaymentViewModel
	```
1.  Put viewmodel provider (which will get the viewmodel class) & observer (which will observe a MutableLiveData of viewmodel) inside the onCreate() of
	```
	paymentViewModel = ViewModelProviders.of(this, viewModelFactory).get(PaymentViewModel::class.java)
        paymentViewModel.paymentUrl.observe(this, Observer { paymentUrl ->
            loadBkashPaymentDialog(paymentUrl)
        })
	```

# Android Advanced

<details>
<summary><strong>The last callback in the lifecycle of an activity is onDestroy(). The system calls this method on your activity as the final signal that your activity instance is being completely removed from the system memory. Usually, the system will call onPause() and onStop() before calling onDestroy(). Describe a scenario, though, where onPause() and onStop() would not be invoked.</strong></summary>
If you detect an error during onCreate() and call finish()
</details>

<details>
<summary><strong>When a LayoutManager asks a RecyclerView to provide a View at position X”, explian briefly the internal processes that take place.</strong></summary>
* Searches changed scrap
* Searches attached scrap
* Searches non-removed hidden views
* Searches the view cache
* If Adapter has stable ids, searches attached scrap and view cache again for given id.
* Searches the ViewCacheExtension
* Searches the RecycledViewPool
* If it fails to find a suitable View in all of the aforementioned places, it creates one by calling adapter’s onCreateViewHolder() method. It then binds the View via onBindViewHolder() if necessary, and finally returns it
</details>

<details>
<summary><strong>Give me a scenario when onCreateViewHolder() & onBindViewHolder() needs to get called in a RecylerView?</strong></summary>
If a ViewHolder can not be found in Scrap, or Pool, or View Cache, RecyclerView calls its adapter's onCreateViewHolder() and then binds the created view by calling onCreateViewHolder() method.
</details>

<details>
<summary><strong>Give me a scenario when onCreateViewHolder() & onBindViewHolder() does not get called in a RecylerView? </strong></summary>
When a ViewHolder is in the view cache, we hope to to reuse it “as-is”, without rebinding, at the same position as the one it was at before it got into the cache.
</details>

<details>
<summary><strong>Give me a scenario when only onBindViewHolder() gets called in a RecylerView? </strong></summary>
If a ViewHolder was found in pool, it is bound.
</details>

<details>
<summary><strong>Suppose you have a News App that shows an Image with a text for each news article preview. It has 2 types of views implemented with RecyclerView. One view is a grid gallery of article previews & the other is a down-scroll feed of article previews. In which view may we need to extend RecyclerView's cache capacity?</strong></summary>
With the given scenario, it's assumable that users would not scroll up/go back to previously read articles too often. So we may need to extend the capacity of the cache in the latter as the grid needs to be updated more frequently.
</details>

<details>
<summary><strong>What method of a RecylerView do we need to call to detect if a certain View is present/visible on the device screen? </strong></summary>
onViewAttachedToWindow() and onViewDetachedFromWindow() callbacks of the RecyclerView's Adapter
</details>

<details>
<summary><strong>What's the difference between the activity lifecycle in a multi-windowed environment where multiple applications are running simultaneously in separate windows?</strong></summary>
There's no difference becaused multi-window mode does not change the activity lifecycle.
</details>

<details>
<summary><strong>Given a scenario of multiple apps running simultaneously in a multi-windowed environment, how to detect which of those application is on top of the other in the back stack of tasks?</strong></summary>
When apps are running simultaneously in a multi-windowed environment, supported in Android 7.0 (API level 24) and higher, the system manages tasks separately for each window; each window may have multiple tasks. Since it's managed by the System as a per-window basis, 2 applications in 2 windows are not in the same back stack of tasks in any way.
</details>

<details>
<summary><strong>What's the highest amount of data that you can keep as a savedInstanceState?</strong></summary>
For the specific case of savedInstanceState, the amount of data should be kept small because the system process needs to hold on to the provided data for as long as the user can ever navigate back to that activity (even if the activity's process is killed). Less than 50k of data in saved state is recommended. [Ref](https://developer.android.com/guide/components/activities/parcelables-and-bundles#sdbp)
</details>
# Resources & Learning Guides

### Android Resources

#### UI
* [Anatomy of RecyclerView: a Search for a ViewHolder](https://android.jlelse.eu/anatomy-of-recyclerview-part-1-a-search-for-a-viewholder-404ba3453714)
* [Anatomy of RecyclerView: a Search for a ViewHolder (continued)](https://android.jlelse.eu/anatomy-of-recyclerview-part-1-a-search-for-a-viewholder-continued-d81c631a2b91#.dcsykhoh9)

#### Best Practices/Demo
* [Sunflower: A gardening app illustrating Android development best practices with Android Jetpack.](https://github.com/android/sunflower)

### LeetCode Resources
* [Read this before you start solving problems on Leetcode (Prep Work)](https://www.alimirio.com/posts/read-this-before-you-start-solving-problems-on-leetcode-prep-work)
* [Best Practice Questions on Leetcode](https://yangshun.github.io/tech-interview-handbook/best-practice-questions)
* [LeetCode Solution Explainer Videos by Nick White](https://www.youtube.com/playlist?list=PLU_sdQYzUj2keVENTP0a5rdykRSgg9Wp-)
* [LeetCode Java solutions by Fisher Coder](https://github.com/fishercoder1534/Leetcode)
