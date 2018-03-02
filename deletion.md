# Deletion

There are a bunch of ways to implement deletion. To actually perform it, you can use the following method.
```
public void deleteNote(int id) {
    // Create a new instance of the NoteTakingDatabase
    NoteTakingDatabase handler = new NoteTakingDatabase(getApplicationContext());
    // Get the writable database
    SQLiteDatabase db = handler.getWritableDatabase();
    // Delete the note from the database
    handler.deleteNote(db, id);
}
```
Remember, you'll probably want to refresh after you do this.

> Note: Remember how you implemented onClickListeners? There's more than just clicking available.