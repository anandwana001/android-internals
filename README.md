# android internals
This repository consists of questions, all about the internal working of android concepts. This will also be helpful in an interview for android developers.

**1. What are the different types of `<activity>` attributes?**
 - [`taskAffinity`](https://developer.android.com/guide/topics/manifest/activity-element.html#aff) - Activities with the same affinity belong to the same task. All activities in an application have the same affinity. The name of the default affinity for an application is the package name
 - [`launchMode`](https://developer.android.com/guide/topics/manifest/activity-element.html#lmode) - Instruction on how the activity should be launched. 
 - [`allowTaskReparenting`](https://developer.android.com/guide/topics/manifest/activity-element.html#reparent) - If allowTaskReparenting is true, it can move from a task into the task it has an affinity for.
 - [`clearTaskOnLaunch`](https://developer.android.com/guide/topics/manifest/activity-element.html#clear) - When this attribute set to true, every time user starts the task will start from the root activity, no matter what user was doing last or whether app back button was pressed or directly home button. It will start always from the root activity.
 - [`alwaysRetainTaskState`](https://developer.android.com/guide/topics/manifest/activity-element.html#always) - When this attribute set to true, user can always hop to the last state of the task.
 - [`finishOnTaskLaunch`](https://developer.android.com/guide/topics/manifest/activity-element.html#finish) - When this attribute set to a true, existing instance of the activity should be shut down whenever the task launches.



**2.  What are the different types of intent flags?** [MindOrks Blog](https://blog.mindorks.com/android-task-and-back-stack-review-5017f2c18196)
 - [`FLAG_ACTIVITY_NEW_TASK`](https://developer.android.com/reference/android/content/Intent.html#FLAG_ACTIVITY_NEW_TASK) - If an Activity does not exist in an already created Task, then it starts the Activity in a new Task with Activity’s new instance at the root of the Task’s back stack, else the Task is brought forward with the Activity’s last state restored and this Activity receives the new intent in onNewIntent method. Only one instance of the Activity can exist at a time. In this case, the Back button is still able to return the user to the previous Task’s Activity.
 - [`FLAG_ACTIVITY_CLEAR_TOP`](https://developer.android.com/reference/android/content/Intent.html#FLAG_ACTIVITY_CLEAR_TOP) - This flag simply clear(`onDestory()`) all other activities running on top of the stack and receive the intent in `onNewIntent()` method. For example - A, B, C, D and D calls B which will make C and D to get clear and left with A, B. 
 - [`FLAG_ACTIVITY_SINGLE_TOP`](https://developer.android.com/reference/android/content/Intent.html#FLAG_ACTIVITY_SINGLE_TOP) - When we want to launch the same activity which is already on the top of the stack but we don't want to create its new instance then we use this flag. If we don't use this flag our back stack will look like this: A, B, C, D, D calling D from D. If we use this flag and calling D from D will look like this: A, B, C, D. If we want to call A from D then our back stack will look like A, B, C, D, A. 
 
**3.  What are the different types of  `launchModes`?**<br>
```
<activity android:launchMode = [“standard” | “singleTop” | “singleTask” | “singleInstance”] ../>
```
 - **Standard** - Default launch mode. New instance of an activity will be created in the same or different tasks. Also, multiple task can be created. A, B, C, D and now starting B which has launch mode standard then our back stack will look like A, B, C, D, B
 - **Single Top** - New instance of an activity will not be created if it already exists on the top of the back stack. 
 - **Single Task** - New instance of an activity will be created in new task if doesn't exist in the already created task else the task brought to the front with the last same state. 
 - **Single Instance** - This is similar as single task but the task holding this activity instance will not any other activity. 

**4.  Navigation between activities?**<br>
If we want results back from the new activity we use `startActivityForResult()` or if we don't want any result we simply use `startActivity()`. We pass intent object as argument to these methods. The result comes back through the `onActivityResult(int, int, Intent)` method.
```
val intent = Intent(this, SignInActivity::class.java)
startActivity(intent)

startActivityForResult(intent , REQUEST_CODE)

override fun onActivityResult(requestCode: Int, resultCode: Int, intent: Intent?) {
        when (requestCode) {
            REQUEST_CODE ->
                if (resultCode == RESULT_OK) {
                    // extract data from intent
                }
        }
    }
```
Going back to previous activity. This will pop the activity from the back stack.
```
override fun onBackPressed() {
    super.onBackPressed()
}
```


**5.  Navigation between fragments?**<br>
**6.  Navigation between activity and fragment?**<br>
**7.  Type of services?**<br>
**8.  Difference between Service and Intent Service?**<br>
**9.  What is  `JobScheduler`?**<br>
**10.  Broadcast Receiver workflow (implicit /explicit both)?**<br>
**11.  Why Constraint Layout comes in pictures (4-5 diff at least)?**<br>
**12.  Different type of contexts?**<br>
**13.  What is retained Fragment?**<br>
**14.  What is  `LocalBroadcastManager`?**<br>
**15.  What is the function of an  `IntentFilter`?**<br>
**16.  What is a Sticky  `Intent`?**<br>
**17.  What is  `PendingIntent`?**<br>
**18.  What are the different types of Broadcasts?**<br>
**19.  How does  `RecyclerView`  works?**<br>
**20.  What is  `DiffUtil`?**<br>
**21.  What is  `attachToParent`  param in the inflate method?**<br>
**22.  Add, Replace difference in a fragment?**<br>
**23.  Commit and Apply difference in Shared Preference?**<br>
**24.  3 parallel async task then what happens UI freeze or not?**<br>
**25.  Memory leaks?**<br>
**26.  Android 10 latest updates/changes?**<br>
**27.  How to reduce APK size?**<br>
**28.  Internal working of  `ViewModel`?**<br>
**29.  Types of  `LiveData`?**<br>
**30.  Final, static, type of exceptions, why inheritance, abstract class, polymorphism diff b/w them, cohesion coupling?**<br>
**31.  Flat map, switch map, concat map, differences?**<br>
**32.  Diff Type of Observable and its uses?**<br>
**33.  Why we need Dependency Injection?**<br>
**34.  Meaning of component, module, inject, the provider?**<br>
**35.  What are their uses?**<br>
**36.  Types of Design Patterns? and example**<br>
**37.  Mvp vs MVVM?**<br>
**38.  How  `ViewPager`  works?**<br>
**39.  Data Binding steps?**<br>
**40.  Why the paging library?**<br>
**41.  `WorkManager`**<br>
**42.  `RxJava`  operators?**<br>
**43.  What is obfuscation?**<br>


### Questions from other resources
- **[Mention two ways to clear the back stack of Activities when a new Activity is called using intent.](https://github.com/anitaa1990/Android-Cheat-sheet)**<br>
The first approach is to use a `FLAG_ACTIVITY_CLEAR_TOP` flag. The second way is by using `FLAG_ACTIVITY_CLEAR_TASK` and `FLAG_ACTIVITY_NEW_TASK` in conjunction.

- **[What’s the difference between FLAG_ACTIVITY_CLEAR_TASK and FLAG_ACTIVITY_CLEAR_TOP?](https://github.com/anitaa1990/Android-Cheat-sheet)**<br>
`FLAG_ACTIVITY_CLEAR_TASK` is used to clear all the activities from the task including any existing instances of the class invoked. The Activity launched by intent becomes the new root of the otherwise empty task list. This flag has to be used in conjunction with `FLAG_ ACTIVITY_NEW_TASK`.<br>
`FLAG_ACTIVITY_CLEAR_TOP` on the other hand, if set and if an old instance of this Activity exists in the task list then barring that all the other activities are removed and that old activity becomes the root of the task list. Else if there’s no instance of that activity then a new instance of it is made the root of the task list. Using `FLAG_ACTIVITY_NEW_TASK` in conjunction is a good practice, though not necessary.
