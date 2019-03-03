# Part 9
## Putting things in a list

Now, our code from Part 8 is giving us errors. This is due to us missing a layout XML file we referenced in our adapter's `newView` method. We need to create a layout for our note list items.

Head into your res -> layouts directory and create a new layout resource file called `note_list_item`. We can leave the root element as the default (we'll change this soon).

Replace what was created by default and insert the following

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="horizontal"
    android:padding="16dp">

    <ImageView
        android:id="@+id/noteImage"
        android:layout_width="32dp"
        android:layout_height="32dp"
        android:src="@android:drawable/btn_dialog" />

    <TextView
        android:id="@+id/noteText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="10dp"
        android:layout_marginStart="10dp"
        android:text="Note Text"
        android:textAppearance="?android:attr/textAppearanceMedium" />
</LinearLayout>
```

Let's break this apart. Our outer element is a `LinearLayout`, another kind of layout that does exactly what it says. Displays thing either horizontally or vertically.

Inside the `LinearLayout` we have an `ImageView` that is used to display an image (our note's image), and a `TextView` that is used to display the note title.

[Let's connect it all together! -->](part10.html)