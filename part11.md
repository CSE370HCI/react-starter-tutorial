# Part 11
## Nothing is there! Lets add notes

You may notice after running this code that nothing displays in your app. You just have a blank page. That's because our `ListView` is empty. We need a way to add notes to our app.

Let's start by adding a button in our menu bar. We'll do this by creating a menu directory in our resources.

1. Right click on the res directory
2. Create new -> "Android resource directory"
3. Select "menu" from the "Resource Type" dropdown
4. Click ok

You should now have a menu directory, right click on it and create a new menu resource file with the name `menu_main.xml`

Put the following in the `menu_main.xml` directory. 
```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context=".MainActivity">
    <item
        android:id="@+id/add_note"
        android:title="Add Note"
        app:showAsAction="ifRoom" />
</menu>
```

A couple notes

> Note #1: This is a menu item, like all layout items we give it an id which we can then refer to it by. On the next line we give it a title. Finally we have `app:showAsAction` that is set to ifRoom. Assuming there's room in the toolbar it will show up otherwise it'll go to the overflow menu.

> Note #2: One assignment will be to add an image to this menu item. You can use the `android:icon` tag and reference a drawable. More on that in a later section.

## Show the menu in our app!

Now that we've created our menu, we want to show it in our main Activity! To do this, head back over to `MainActivity`. Copy and paste the following lines.

```
@Override
public boolean onOptionsItemSelected(MenuItem item) {
    switch (item.getItemId()) {
        case R.id.add_note:
            // TODO something
            return true;
        default:
            return super.onOptionsItemSelected(item);
    }
}

@Override
public boolean onCreateOptionsMenu(Menu menu) {
    getMenuInflater().inflate(R.menu.menu_main, menu);
    return super.onCreateOptionsMenu(menu);
}
```

The following two methods are required for two reasons. The bottom `onCreateOptionsMenu` tells our Activity that when the menu is created, inflate our layout `R.menu.menu_main` and show that in the menu bar.

The next method `onOptionsItemSelected` handles what we want to do with each item when it is clicked. After this tutorial, if you'd like to add more menu items, this is how you'll do it.

In the next step we'll open up a brand new activity when we click this.

[Head to Part 12! ->](part12.html)