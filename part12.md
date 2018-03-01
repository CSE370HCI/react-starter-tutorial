# Part 11
## Going from one Activity to Another

We need another Activity that will let us create a note. We can create a new activity by right clicking on our package (inside our java directory), New -> Activity -> Empty Activity

We'll name it "NoteActivity" for this demo.

Copy and paste the following global variables to the top of our new class.

```
String imagePath = "";
Button saveNote;
TextView noteTitle;
ImageView noteImage;

SQLiteDatabase db;

boolean isUpdate = false;
int noteId;
```

These are all things we'll need, now **copy and paste** the following methods.

```
private void updateNote(int noteId, String imagePath, String title, String description) {
    // Create a new instance of the NoteTakingDatabase
    NoteTakingDatabase handler = new NoteTakingDatabase(getApplicationContext());
    // Get the writable database
    SQLiteDatabase db = handler.getWritableDatabase();
    // Store the note in the database
    handler.updateNote(db, noteId, imagePath, title, description);
}

private void setNote(Integer noteId) {
    // Get note by id
    Cursor cursor = db.rawQuery("SELECT * FROM notes WHERE _id = " + noteId, null);
    cursor.moveToFirst();

    // Set note details to view
    String path = cursor.getString(cursor.getColumnIndexOrThrow("noteImage"));
    Bitmap bitmap = BitmapFactory.decodeFile(path);
    noteImage.setImageBitmap(bitmap);

    // Get the note text from the database as a String
    String noteText = cursor.getString(cursor.getColumnIndexOrThrow("noteText"));
    noteTitle.setText(noteText);

    cursor.close();
}

public void storeNote(String path, String title, String description) {
    // Create a new instance of the NoteTakingDatabase
    NoteTakingDatabase handler = new NoteTakingDatabase(getApplicationContext());
    // Get the writable database
    SQLiteDatabase db = handler.getWritableDatabase();
    // Store the note in the database
    handler.storeNote(db, path, title, description);
}
```

These are all functions we can use to update and store notes. The `setNote` method will take in an `id` and update the view with the note's values.

## Creating the View
When we created this new activity, a layout file was automatically generated. Open up the res->layout->`activity_note.xml` layout.

Here's the layout we'll use for this tutorial. It contains and `ImageView` and two `TextView` elements. We'll use these to pick our note image, title, and description. As well as a button for creating a note.

```
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_marginEnd="8dp"
    android:layout_marginStart="8dp"
    android:layout_marginTop="8dp">

    <ImageView
        android:id="@+id/note_image"
        android:layout_width="66dp"
        android:layout_height="64dp"
        android:layout_marginBottom="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintBottom_toBottomOf="@+id/note_description"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <EditText
        android:id="@+id/note_title"
        android:layout_width="282dp"
        android:layout_height="wrap_content"
        android:hint="Note Title"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/note_image"
        app:layout_constraintTop_toTopOf="parent" />

    <EditText
        android:id="@+id/note_description"
        android:layout_width="282dp"
        android:layout_height="wrap_content"
        android:ems="10"
        android:hint="Note Description"
        android:inputType="textMultiLine"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/note_image"
        app:layout_constraintTop_toBottomOf="@+id/note_title" />

    <Button
        android:id="@+id/create_note"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Create Note"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />
</android.support.constraint.ConstraintLayout>
```

## How do we open this new view?
Alright, we've got our first and second Activities now, we just need to open one from the other. To do that we'll use something called an `Intent`. You can think of it like this.

An intent is like saying: my intent is to go from one activity to another. But it can also be used to open URLs, share data, and more! In this case we'll use it to open a new activity.

In your MainActivity java code under our Overridden `onOptionsItemSelected` where we have `// TODO open a new activity` we'll write the following code.

First, add the following line

```
Intent intent = new Intent(MainActivity.this, NoteActivity.class);
```
This is how we create a new intent. Passing in the activity we're currently in, then the class we want to go to.
After, you can specify any data you want to pass along, which we will do later.

Next we just need 
```
startActivity(intent);
```

Boom! When we click on the menu item now, we'll be taken to the new activity!

[We're almost there! Head to the next section and we'll actually create the notes! ->](part13.html)