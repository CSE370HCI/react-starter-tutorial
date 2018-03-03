# Part 14
## Getting read to add images - Permissions

Writing the code to add image support is a little bit more than just a couple lines. First, I'll explain how permissions work.

Starting in recent Android versions, the app developer (you) needs to request permission for using certain things. For example, taking pictures will require us to store images in a specific folder so we can retrieve them at a later date. 

Because of that, we need to ask for permission to access the user's files, this way we can write to them. This is a couple step process, so we'll start in the `MainActivity`.

For simplicity, we'll simply ask for permission when the user loads the notes. 

In your `MainActivity` under `onCreate` we have a line called `loadNotesFromDatabase();`, we'll be adding a conditional (if statement) around that.

1. Before we do that, we'll need to check if the user has permission. You can copy and paste the following method
    ```
    public boolean userHasPermission() {
        return ContextCompat.checkSelfPermission(getApplicationContext(), Manifest.permission.WRITE_EXTERNAL_STORAGE) == PackageManager.PERMISSION_GRANTED;
    }
    ```
    and then create an if statement. If true, the user has permission, if false, we need to request it.

2. If the user does have permission, we can let use `loadNotesFromDatabase();` like before.
3. If the user does not have permission, we'll need an extra line
    ```
    ActivityCompat.requestPermissions(MainActivity.this,
            new String[]{Manifest.permission.WRITE_EXTERNAL_STORAGE},
            0);
    ```
4. Copy and paste the following method into this project
    ```
    @Override
    public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);
        switch (requestCode) {
            case 0:
                if (grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                    Toast.makeText(getApplicationContext(), "Permission Granted", Toast.LENGTH_SHORT).show();
                    loadNotesFromDatabase();
                } else {
                    // TODO tell the user we need permission for our app to work
                }
                break;
        }
    }
    ```
    This overriden method will be called when the user selects either Accept Permission or Deny Permission.

    > Note: In this we use a `Toast` to display a message. For more on this you can see the documentation for [Toasts](https://developer.android.com/guide/topics/ui/notifiers/toasts.html) and also [Snackbars](https://developer.android.com/training/snackbar/action.html).

Now let's run it and we should get this notification!

![Our app asking for permissions](https://i.imgur.com/M10q44h.png)

[Next step! Let's add image! ->](part15.html)