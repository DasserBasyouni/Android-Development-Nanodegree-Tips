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
