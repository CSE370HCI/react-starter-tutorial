# Part 15
## Adding Libraries & Image Support

To add all the functionality we want for images, we'll be using a library to make our lives easier. Adding a library in Android is incredibly easy. In our case we need to add two lines to two files.

There are two `build.gradle` files. Open both of them, one should show up as "app" and one should show up as the name of your project.

In the one that shows up as the name of your project there should be a parameter with the following in it:
```
allprojects {
    repositories {
        google()
        jcenter()
    }
}
```

Right under `jcenter()` add the following line `maven { url 'https://jitpack.io' }`. This will make it so you can use the package we need.

In the other `build.gradle` file, there's a list of dependencies that start with `implementation`. Under one of them add the following line.

```
implementation 'com.github.jkwiecien:EasyImage:1.3.1'
```

A dialog should show asking you to "Sync Now", click it and wait for it to load. You now have added the EasyImage library!

> Note: You can find the complete EasyImage documentation here - https://github.com/jkwiecien/EasyImage

## Using the library
Now open up your `NoteActivity` activity so we can allow the user to pick an image and set it. 

Notice the code for adding a click listener to our `Button`. We can use pretty much that same code to add a listener to the `ImageView`. You can add the following code to your `onCreate`.

```
noteImage.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        // Use the EasyImage library to open up a chooser to pick an image.
        EasyImage.openChooserWithGallery(NoteActivity.this, "Upload an Image", 0);
    }
});
```

By calling `openChooserWithGallery` we pass in our current activity, the title of the dialog we want, and an identifying `Integer`. Now, we need to handle the callback from that, similar to the way we handled permissions.

Add the following method to your code.

```
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);

    EasyImage.handleActivityResult(requestCode, resultCode, data, this, new DefaultCallback() {
        @Override
        public void onImagePickerError(Exception e, EasyImage.ImageSource source, int type) {
            // TODO error stuff
        }

        @Override
        public void onImagePicked(File imageFile, EasyImage.ImageSource source, int type) {
            imagePath = imageFile.getAbsolutePath();
            Bitmap imageBitmap = BitmapFactory.decodeFile(imagePath);
            noteImage.setImageBitmap(imageBitmap);
        }
    });
}
```

This method gets called when the user picks an image. If there was an error, we should show something. If there wasn't and an image was picked, we're going to set the path of the image into a variable and show the image in our ImageView.

![Boom](https://i.imgur.com/AVTwUcO.png)
Boom!

[Let's implement editing -->](part16.html)