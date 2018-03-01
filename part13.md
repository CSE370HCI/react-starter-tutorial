# The code to create a new Note

Alright, we now have two activities with their appropriate layouts and we have some methods that will allow us to create notes. Let's hook it all together.

**Before we begin**
We need to add a small snipit of code to our `onCreate` in our `NoteActivity` so our database code will function. Add the following two lines (below `setContentView`).
```
// Create a new instance of the NoteTakingDatabase
NoteTakingDatabase handler = new NoteTakingDatabase(getApplicationContext());
// Get the writable database
db = handler.getReadableDatabase();
```
As usual, we need to get references to our `ImageView`, `EditText`, and `Button`. So we'll use `findViewById` to get those references. This will all go in our onCreate.
```
saveNote = findViewById(R.id.create_note);
noteTitle = findViewById(R.id.note_title);
noteImage = findViewById(R.id.note_image);
```

Now we have our elements defined and can use them. Let's handle a button click! We called our button `saveNote` so we can type `saveNote.se`... and at this point Android Studio will most likely suggest `setOnClickListener`, if it does, press enter, then inside the parenthesis type `new OnClickListener` and again, Android Studio will most likely autosuggest this. If it does, press enter again and Android Studio will autofill your needed code.

If it doesn't auto generate, you can just copy and paste.

```
saveNote.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        
    }
});
```

> Note: You can usually press Ctrl+Space to have Android Studio auto suggest things.

Now, anything we put inside the onClick function will run when the `Button` is clicked. Let's put the following code inside.

`storeNote("", noteTitle.getText().toString(), "");`

Right now, we're leaving the image and description empty. The description will be an exercise for you and the image will come later. Let's run this, put something in the title, and click save. Since we haven't implemented refreshing we'll need to close the app and reopen it.

For some help implementing refreshing, go here [Refreshing Tutorial - Assignment Part](refreshing.html).

We'll now see something in our list! Finally!