# Part 7
## Creating our App

In this tutorial we will be creating the basis for a note taking app. This tutorial will have the following features and focus on design and less on the backend.

- Creating and editing notes
- Adding images to notes
- Adding descriptions to notes

It will also provide code snippits for the following features
- Deleting notes
- Refreshing note lists

## The Layout

Lets start by modifying our Hello World layout to display a list of Notes we'll provide. To start, open up the `activity_main.xml`. Remove the `TextView` element.

We're now going to add a `ListView` element. Open up the XML of our layout and copy and paste the following (in place of the `TextView`).

```
<ListView
    android:id="@+id/note_list"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```
This is a ListView, it fills the whole view and has an id of note_list. The ID is important as it's how we access all references to our layout.

If you run this project now, you'll see nothing, since it's an empty list.

## ONE LAST THING!
One last thing! We need to tell our app that it wants permission to write to the external storage of our app. We'll need this for when start storing images.

To do so, we need to open up our `AndroidManifest.xml` file in our src->main package. Right above the `<application>` tag (or right below the start of the `<manifest` tag), add the following line. 

```
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

[Head to part 8 to learn how to add items to a list -->](part8.html)