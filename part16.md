# Part 16
## Editing Messages

Almost done! We need to make sure the user can click and edit a message. To do this we'll open the NoteActivity and pass in a parameter so we know we're editing.

First, let's add a click listener to our `ListView` items, this is a little different than before, but almost the same.

In your `MainActivity`'s `onCreate` after you define your noteList `ListView`, put the following.
```
noteList.setOnItemClickListener(new AdapterView.OnItemClickListener() {
    @Override
    public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
        //TODO open the new dialog.
    }
});
```

Now let's use an `Intent` and pass in some data to open the `NoteActivity`. Replace the `TODO` statement with the following lines.

```
Intent openNote = new Intent(MainActivity.this, NoteActivity.class);
openNote.putExtra("noteId", id);
startActivity(openNote);
```

This will open the `NoteActivity` when you click on any item, but we need to handle it on the other side. Let's now open up our `NoteActivity` activity and check to see if there exists a noteId. If there is, then we know we're supposed to be editing it.

```
Bundle extras = getIntent().getExtras();
if (extras != null) {
    isUpdate = true;
    noteId = (int) extras.getLong("noteId");
    setNote(noteId);
}
```

The snippit will get the `Intent` extras we sent along with the request. If there are extrasa, we get the noteId and set it to a variable, then we pass it into the function `setNote` that sets all the values of our layout with the stored note's information.

Finally, one more thing we need to do. Previously we just had a single line when you clicked "Create Note", now we'll add some logic to either Create or Update a note. You can replace the line `storeNote("", noteTitle.getText().toString(), "");` with the following.

```
if (!isUpdate) {
    storeNote(imagePath, noteTitle.getText().toString(), "");
} else {
    updateNote(noteId, imagePath, noteTitle.getText().toString(), "");
}
finish();
```

That will either update or store the note, and then close that `Activity` and return you to the `MainActivity`.

[Head. To. The. Conclusion! You made it! ->](conclusion.html)