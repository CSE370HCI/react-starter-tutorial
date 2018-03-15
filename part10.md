# Part 10
## Connecting it all together

Now let's put it all together! We should now have a database and adapter all set up without errors, we just need to implement them! Let's start by heading over to our MainActivity class.

First let's add some global variables to our class. Add the following variables to the top of your class.

```
Cursor todoCursor;
ListView noteList;
NoteAdapter adapter;
```

Next we'll reference our `ListView` from our activity. We do this by using a method called `findViewById` which will let us get the `ListView` by the id we previous gave it.
Below `setContentView` add the following line.

```
noteList = (ListView) findViewById(R.id.note_list);
```

> Note: When using `findViewById` we need to cast the `View` to whatever type of View element it is, in this case a `ListView`. In newer version of the Android SDK this cast is not required. Android Studio will tell you if that's the case.

This code will now let us use noteList and have the changes reflected in our UI.

Next we'll create a function that connects our ListView, Adapter, and Database all together. Copy and paste the following function into your MainActivity.

```
public void loadNotesFromDatabase() {
    // Create a new instance of the NoteTakingDatabase
    NoteTakingDatabase handler = new NoteTakingDatabase(getApplicationContext());
    // Get the writable database
    SQLiteDatabase db = handler.getWritableDatabase();
    //Get all notes from the database
    todoCursor = db.rawQuery("SELECT * FROM notes", null);

    // Create an instance of the NoteAdapter with our cursor
    adapter = new NoteAdapter(this, todoCursor, 0);

    // Set the NoteAdapter to the ListView (display all notes from DB)
    noteList.setAdapter(adapter);
}
```
You can reference the comments for a line by line explanation of what this does. But essentially. It selects all of the notes from our database, passes that database cursor to our adapter, and sets the adapter of our ListView so it will show the notes.

Now, all we need to do is add `loadNotesFromDatabase();` right after we declare the `ListView` in our `onCreate` and any notes in our database will populate into our ListView!

## One quick note
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

[Head to Part 11! -->](part11.html)