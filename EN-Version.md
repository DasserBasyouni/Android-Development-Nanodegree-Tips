# Android Development Nanodegree Tips

1. If the class will never be extended, so you can mark the class as final  
Example Utils.class  
Related: [Use of final class in Java
](https://stackoverflow.com/questions/5181578/use-of-final-class-in-java
 )

2. If the class will never be instantiated, so you can suppress the constructor.  
`private Utils() {}`  
Related: [Why java.util.Objects private constructor throws assertionError
](https://stackoverflow.com/questions/25658330/why-java-util-objects-private-constructor-throws-assertionerror)

3. Organize your code by using descriptive packages.  
For example, you can store your "Adapter" classes in a package named "adapter"  
Related: [Package - JavaPoints.com
](https://www.javatpoint.com/package)

4. Improve the efficiency of your Adapter by using the ViewHolder pattern  
Related: [Making ListView Scrolling Smooth #ViewHolder](https://developer.android.com/training/improving-layouts/smooth-scrolling.html#ViewHolder)  
This works by caching Views; so findViewById() only has to be called once per view. You can find a detailed tutorial here:   [Optimizing Your ListView with the ViewHolder Pattern](https://dzone.com/articles/optimizing-your-listview)

5. Package names should be all lowercase to avoid confusing it as a class or interface.

6. Method names should be camelCase by convention and contain no underscores.

7. Class names should be UpperCamelCase by convention.

8. Fields are typically placed at the top of the class. The structure is usually like this:  
<\</FIELDS>\>  
<\<CONSTRUCTORS>\>  
<\<METHODS>\>  
This makes the class structure predictable. [See this guide for more common standards](https://google.github.io/styleguide/javaguide.html) 

-----------
**Questions asked to mentors**

// Baking App
1. I allowing allowMainThreadQueries() to do those widget queries, is there is a better way?  (In Baking App widget)
Yes. You should refrain from doing anykind of long running operation on the UI thread, since it can block it. You would want to move it off of the main thread. Previously you would use something like a Loader, but they have recently been deprecated so the recommended approach is to use a combination of [LiveData](https://developer.android.com/topic/libraries/architecture/livedata) and [ViewModel.]( 
https://developer.android.com/topic/libraries/architecture/viewmodel)

2. according to [Recommended way for releasing and recreating the player?](https://github.com/brianwernick/ExoMedia/issues/425)
is this the appropriate way ?
The proper way is to release the assets manually. The referenced link is actually a library that wraps the ExoPlayer. The setup you are using won't actually release the assets automatically. ExoMedia and ExoPlayer are two different things. ExoMedia is actually a library that wraps ExoPlayer. If it can't use ExoPlayer then it uses VideoView. SimpleExoPlayer in this case has to be released manually.

3. LIKE in Room is returning null, code:  
 `@Query("SELECT ingredients FROM recipe_db WHERE id LIKE :id LIMIT 1")
 String getRecipeIngredients(int id);`  
 This is happening because the SQL is setup incorrectly. You want to set it up so it matches the passed in ID. The LIKE clause works differently and uses pattern matching symbols.  
Related: [My Stack-overflow Question](https://stackoverflow.com/questions/50918340/room-persistence-library-query-not-working/51164049#51164049)

4. when the phone rotates the progress-bar visibility goes to Visible again, how to disable that?  
On rotation, a Loader honors the lifecycle. The default state of the progressBar is visible. You can use something like onSaveInstanceState() and onRestoreInstanceState() to manage it based on the data provided by the Loader
