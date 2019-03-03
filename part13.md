# Part 13
## The code to create a new Note

Alright, we now have two activities with their appropriate layouts and we have some methods that will allow us to create notes. Let's hook it all together.

**Before we begin**
We need to add a small snipit of code to our `onCreate` in our `NoteActivity` so our database code will function. Add the following two lines (below `setContentView`).
```
// Create a new instance of the NoteTakingDatabase
NoteTakingDatabase handler = new NoteTakingDatabase(getApplicationContext());
// Get the writable database
db = handler.getReadableDatabase();
```
> This code will get the app's database instance and store it in the `db` variable for us to use in this activity.

As usual, we need to get references to our `ImageView`, `EditText`, and `Button`. So we'll use `findViewById` to get those references. This will all go in our onCreate.
```
saveNote = (Button) findViewById(R.id.create_note);
noteTitle = (TextView) findViewById(R.id.note_title);
noteImage = (ImageView) findViewById(R.id.note_image);
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

`storeNote(imagePath, noteTitle.getText().toString(), "", "");`

Right now, we're leaving the description and category empty. The description and category will be an exercise for you. Let's run this, put something in the title, and click "Create Note". Since we haven't implemented refreshing we'll need to close the app and reopen it. 

> Note: If you're unfamiliar with Android devices, press the back arrow twice, then click on the app from the app drawer (swipe up from the bottom app row). 

For some help implementing refreshing, go here [Refreshing Tutorial - Assignment Part](refreshing.html).

We'll now see something in our list! Finally! Here's what you should see after making a note.

![Our app](https://i.imgur.com/x9ibQTZ.png)

[Next, let's add image support](part14.html)