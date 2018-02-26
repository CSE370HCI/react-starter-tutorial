# Part 3
## Layouts

Let's look inside the `activity_main.xml` layout. When we open it in Android Studio, we see two views. "Design" and "Text"

First let's open the "Design" section, we see something like this.

![Layouts, bam](https://i.imgur.com/Llk5BQP.jpg)
Let's break this apart. On the left side we see a Palette. These contain all the different types of inputs, text, views, layouts etc. Right now, we're defaulted with a TextView. Let's start with that and go from there.

Below the Pallete we see a "Component Tree", this shows us what's in our current Activity. Like I said, we have a TextView inside a "ConstraintLayout". ConstraintLayout is a new layout from Google that allows all elements to be constrained in the view somewhat relative to their surroundings.
