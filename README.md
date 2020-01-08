# android internals
This repository consists of questions, all about the internal working of android concepts. This will also be helpful in an interview for android developers.

1. What are the different types of `<activity>` attributes?
 - [`taskAffinity`](https://developer.android.com/guide/topics/manifest/activity-element.html#aff) - Activities with the same affinity belong to the same task. All activities in an application have the same affinity. The name of the default affinity for an application is the package name
 - [`launchMode`](https://developer.android.com/guide/topics/manifest/activity-element.html#lmode) - Instruction on how the activity should be launched. 
 - [`allowTaskReparenting`](https://developer.android.com/guide/topics/manifest/activity-element.html#reparent) - If allowTaskReparenting is true, it can move from a task into the task it has an affinity for.
 - [`clearTaskOnLaunch`](https://developer.android.com/guide/topics/manifest/activity-element.html#clear) - When this attribute set to true, every time user starts the task will start from the root activity, no matter what user was doing last or whether app back button was pressed or directly home button. It will start always from the root activity.
 - [`alwaysRetainTaskState`](https://developer.android.com/guide/topics/manifest/activity-element.html#always) - When this attribute set to true, user can always hop to the last state of the task.
 - [`finishOnTaskLaunch`](https://developer.android.com/guide/topics/manifest/activity-element.html#finish) - When this attribute set to a true, existing instance of the activity should be shut down whenever the task launches.


<br></br>
2.  What are the different types of intent flags?
3.  What are the different types of  `launchModes`?
4.  Navigation between activities?
5.  Navigation between fragments?
6.  Navigation between activity and fragment?
7.  Type of services?
8.  Difference between Service and Intent Service?
9.  What is  `JobScheduler`?
10.  Broadcast Receiver workflow (implicit /explicit both)?
11.  Why Constraint Layout comes in pictures (4-5 diff at least)?
12.  Different type of contexts?
13.  What is retained Fragment?
14.  What is  `LocalBroadcastManager`?
15.  What is the function of an  `IntentFilter`?
16.  What is a Sticky  `Intent`?
17.  What is  `PendingIntent`?
18.  What are the different types of Broadcasts?
19.  How does  `RecyclerView`  works?
20.  What is  `DiffUtil`?
21.  What is  `attachToParent`  param in the inflate method?
22.  Add, Replace difference in a fragment?
23.  Commit and Apply difference in Shared Preference?
24.  3 parallel async task then what happens UI freeze or not?
25.  Memory leaks?
26.  Android 10 latest updates/changes?
27.  How to reduce APK size?
28.  Internal working of  `ViewModel`?
29.  Types of  `LiveData`?
30.  Final, static, type of exceptions, why inheritance, abstract class, polymorphism diff b/w them, cohesion coupling?
31.  Flat map, switch map, concat map, differences?
32.  Diff Type of Observable and its uses?
33.  Why we need Dependency Injection?
34.  Meaning of component, module, inject, the provider?
35.  What are their uses?
36.  Types of Design Patterns? and example
37.  Mvp vs MVVM?
38.  How  `ViewPager`  works?
39.  Data Binding steps?
40.  Why the paging library?
41.  `WorkManager`
42.  `RxJava`  operators?
43.  What is obfuscation?
