# Part 4
## The Java Files

Now let's look at our `MainActivity.java`. This is already connected to our XML file so we don't need to do that manually. Right now our code looks like this:

```
package com.tristanwiley.cse410;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```

## Before we continue
Before we continue, we should add a quick method to our MainActivity, this will ensure that our database doesn't crash our app when we close the app.

```
@Override
protected void onDestroy() {
    super.onDestroy();
    // Close database cursor
    if (todoCursor != null) {
        todoCursor.close();
    }
}
```

**Continuing**

The first few lines are pretty ordinary, our package name and import statements. We have our MainActivity class that extends [AppCompatActivity](https://developer.android.com/reference/android/support/v7/app/AppCompatActivity.html) which is essentially an Android activity that's compatible with previous versions.

Next, we have an Overriden `onCreate` function. This is what gets called whenever our app's activity is first created. 

> Note: Android has an odd lifecycle, if you're interested in learning more you can check out [this image](https://developer.android.com/guide/components/images/activity_lifecycle.png).

Continuing, we have `setContentView(R.layout.activity_main)`. This connects with our `activity_main` layout that we were just looking at in [Part 3](part3.html).

Now let's try running this!

[*GO TO PART 5 ->*](part5.html)