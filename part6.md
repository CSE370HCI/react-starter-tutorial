# Part 6
## How do we debug?

In normal Java programs debugging is just looking at the console output. Android apps are very similar. Instead of the "Output" we have the **Logcat**.

Look at the bottom of Android Studio, you'll see a few panes, one will say Logcat.
![Logcat](https://i.imgur.com/UdpjgcW.jpg)

> Note: If you don't see the LogCat by default, you can show it by either going to `View -> Tool Windows -> Logcat` or simply pressing `Alt+6`.

The LogCat is where the output of your app will go (and all other apps, if unfiltered).

### Some quick notes:
If we want to Log to the LogCat for debugging we can use `Log`. 

For example, `Log.w("TAG", "MESSAGE")` will print out a warning to the output. 

You can also use `Log.v` for Verbose, `Log.e` for an error, and even [`Log.wtf`](https://developer.android.com/reference/android/util/Log.html#wtf(java.lang.String, java.lang.String, java.lang.Throwable)) for "What a Terrible Failure: Report an exception that should never happen."

**What does a crash look like?**

Here I forced a crash with some pretty bad code. This is what it looks like in the LogCat
![Bad error booo crash](https://i.imgur.com/tbeo6wR.jpg)

There's really only ever a couple lines pertaining to what we need

```
    java.lang.RuntimeException: Unable to start activity ComponentInfo{com.tristanwiley.cse410/com.tristanwiley.cse410.MainActivity}: java.lang.NullPointerException: Attempt to invoke virtual method 'java.lang.String java.lang.String.toLowerCase()' on a null object reference
        at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2778)
        at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:2856)
        at android.app.ActivityThread.-wrap11(Unknown Source:0)
        at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1589)
        at android.os.Handler.dispatchMessage(Handler.java:106)
        at android.os.Looper.loop(Looper.java:164)
        at android.app.ActivityThread.main(ActivityThread.java:6494)
        at java.lang.reflect.Method.invoke(Native Method)
        at com.android.internal.os.RuntimeInit$MethodAndArgsCaller.run(RuntimeInit.java:438)
        at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:807)
    Caused by: java.lang.NullPointerException: Attempt to invoke virtual method 'java.lang.String java.lang.String.toLowerCase()' on a null object reference
        at com.tristanwiley.cse410.MainActivity.onCreate(MainActivity.java:15)
        at android.app.Activity.performCreate(Activity.java:6999)
        at android.app.Activity.performCreate(Activity.java:6990)
        at android.app.Instrumentation.callActivityOnCreate(Instrumentation.java:1214)
        at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2731)
        at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:2856) 
        at android.app.ActivityThread.-wrap11(Unknown Source:0) 
        at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1589) 
        at android.os.Handler.dispatchMessage(Handler.java:106) 
        at android.os.Looper.loop(Looper.java:164) 
        at android.app.ActivityThread.main(ActivityThread.java:6494) 
        at java.lang.reflect.Method.invoke(Native Method) 
        at com.android.internal.os.RuntimeInit$MethodAndArgsCaller.run(RuntimeInit.java:438) 
        at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:807) 
```

The first line tells us that there was a NullPointerException when trying to call toLowerCase() on something. 

> Note: You'll notice in the screenshot that one link in the LogCat is blue. If you click on that it will *usually* take you directly to the issue. Which as you can see, is on line 15 of our MainActivity..

[*GO TO PART 7 ->*](part7.html)