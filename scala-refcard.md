Refcard \#164

**Getting Started With Scala**

A General-Purpose Programming Language

Original by Ryan Knight & Nilanjan Raychaudhuri

**SECTION 1**

**What is Scala?**

Scala is a general-purpose programming language designed to express common programming patterns in a concise, elegant, and type-safe way. It smoothly integrates features of object-oriented and functional programming languages, enabling programmers to be more productive. Scala is an acronym for “Scalable Language”. This means that Scala grows with you.

An important aspect of Scala is that it runs inside the JVM. That means it can leverage existing Java Libraries and libraries written in Scala can be called from Java.

**SECTION 2**

**Create a New Scala Project Using Activator**

The easiest way to get started with Scala is with Typesafe Activator—an open source tool for starting new projects using the Typesafe Platform. To get started:

1.  Typesafe Activator:\
    [typesafe.com/platform/getstarted](https://dzone.com/refcardz/typesafe.com/platform/getstarted)

2.  Follow the instructions on the download page to launch Activator

3.  Create a new application using the “Hello Scala 2.11!” template application

If you are using the UI then Activator will automatically run your application. You can go under the "Run” menu on the left-hand side to see the output: Hello World.

![](/Users/ryan/Documents/temp/images/media/image1.png){width="6.5in" height="3.683333333333333in"}

You can either use the basic code editor in Activator or open your project in IntelliJ or Scala IDE for Eclipse. In the Activator UI go to Code, then select “Open In” to generate the project files for your IDE.

Your new project has the following layout:

src/main/scala - The source directory for the main Scala files

src/test/scala - The test directory for the main Scala files

build.sbt - The project build file. The details of build.sbt will be covered in the Build section later on.

**SECTION 3**

**Hello Scala – An Intro Tour of Scala Features**

The most important feature of Scala is that it tends to be very enjoyable. This is because there is no boilerplate code and a lightweight syntax, but at the same time it has the safety of a strong static type system.

Let's say hello to Scala by modifying the Hello.scala file either in Activator or in an IDE. In Activator the code is automatically run after the file is changed and saved (Ctrl + S).

In Scala, variables can either be mutable or immutable. An immutable variable is a variable that cannot be modified after it has been created. There are a number of reasons for using immutable variables.For instance, they are inherently thread-safe. Another reason is that they are easier to reason about because you know the value cannot change. The best practice is to start off with an immutable variable and only make it mutable if needed.

To create an immutable variable you preface it with the keyword val and mutable variables are created with the keyword var. In the Hello.scala file let's start by creating an immutable String variable called first and printing it out:

![](/Users/ryan/Documents/temp/images/media/image2.png){width="6.5in" height="0.7138888888888889in"}

If you are running this in Activator, after you save the file go to the Activator Run tab to see the results.

To understand what it means to be immutable, try assigning the variable first to a new value:

![](/Users/ryan/Documents/temp/images/media/image3.png){width="6.5in" height="0.5229166666666667in"}

When you save it, the editor will mark the error by underling the problem line.To see the error message mouse over to the red “x” marker on the left. The error that is displayed is:

![](/Users/ryan/Documents/temp/images/media/image4.png){width="6.5in" height="0.5159722222222223in"}

Now let's change first to be a mutable variable by going back up and changing the val to var and saving the program. This time the program compiles and if you print out the first variable after changing the value you will see the changed value.

Continuing the exploration of Scala features, let's look next at type inference, which means the Scala compiler infers the type of a variable. This allows the programmer to omit certain types annotations. To see this in action change the declaration of the first variable by removing the type:

![](/Users/ryan/Documents/temp/images/media/image5.png){width="6.5in" height="0.4777777777777778in"}

What you will notice is that the program still compiles. The Scala compiler has inferred first as a String because it was assigned a String value. This is different than a dynamic language like JavaScript that allows the type of the variable to change. In Scala you cannot change the type of the variable after it has been declared. For example, try assigning first to a number:

![](/Users/ryan/Documents/temp/images/media/image6.png){width="6.5in" height="0.4875in"}

You will get a type mismatch error saying the compiler found an Int but it required a String. Be sure to delete this line so your sample will continue to compile.

Type Inference is really powerful in Scala and can be used to infer the type of variables, methods, functions, and other expressions. It should be used with some caution though, as the Scala Style Guide (http://docs.scala-lang.org/style/types.html) says:

“Use type inference where possible, but put clarity first, and favor explicitness in public APIs.”

Another feature that makes Scala unique is that it is fully expression-oriented. For example, let's create an Int (an integer type in Scala) variable and assign it to the result of a basic calculation:

![](/Users/ryan/Documents/temp/images/media/image7.png){width="6.5in" height="1.1208333333333333in"}

This assigns a value of 98 to second. Notice that it does not require an explicit return statement and instead takes the last line to be the value returned. In the same way, an if-else is an expression in Scala and yields a result. We could create a String variable displayFlag that is the result of a basic if-else test:

![](/Users/ryan/Documents/temp/images/media/image8.png){width="6.5in" height="1.6041666666666667in"}

Or in shorthand notation this could be expressed as:

![](/Users/ryan/Documents/temp/images/media/image9.png){width="6.5in" height="0.9465277777777777in"}

Lets now dive in-depth into some more Scala features.

**SECTION 4**

**Classes and Objects**

Scala is a pure object-oriented language. Conceptually, every value is an object and every operation is a method call. You can follow along with the below examples by creating an additional file in the editor that has the same name as the class. For example, to create a class Recipe add a Recipe.scala file in the src/main/scala directory and then add the following definition in the file:

![](/Users/ryan/Documents/temp/images/media/image10.png){width="6.5in" height="1.0625in"}

This creates a Scala class called Recipe with a constructor that takes calories as a parameter. Unlike Java, the constructor arguments are included in the class definition. Then any expressions in the body of the class are considered part of the "primary constructor", such as the println. If you need alternative ways to create instances of the class, you can define secondary constructors with different arguments, but that is not covered here.

In addition to constructor parameters, a class has fields, such as cookTime in the previous example. These fields can either be a val or var just like a standard variable declaration. By default the constructor parameters for a class are only visible inside the class itself and only fields are visible outside of the class. To understand the differences back in the Hello main, try creating an instance of Food by invoking the primary constructor and then try printing out the values from the class:

![](/Users/ryan/Documents/temp/images/media/image11.png){width="6.5in" height="1.6604166666666667in"}

To promote the constructor parameters to fields, a val or var needs to be added in front of the parameter depending on whether they are supposed to be immutable or mutable fields. For example, change the Recipe class definition to:

![](/Users/ryan/Documents/temp/images/media/image12.png){width="6.5in" height="0.48055555555555557in"}

Then try printing out the calories again in the main method. Now the compiler should be happy.

Method definitions in Scala start with the keyword def followed by the name of the method and its parameters. The return type of the method can be inferred, just like with variables. The following defines a method estimatedEffort that calculates the estimated effort for the recipe based on the number of servings and returns per Int. The return value is the last line of the method.

![](/Users/ryan/Documents/temp/images/media/image13.png){width="6.5in" height="1.4180555555555556in"}

We can also create subclasses by extending abstract or non-final classes just like any object-oriented language. The one difference is the constructor parameters of the class being extended need to be passed in as well.

![](/Users/ryan/Documents/temp/images/media/image14.png){width="6.5in" height="0.8645833333333334in"}

When extending a class we can also override members of parent classes.

![](/Users/ryan/Documents/temp/images/media/image15.png){width="6.5in" height="3.1791666666666667in"}

Scala does not have a static keyword like Java to mark a definition as a static (singleton) instance. Instead it uses the object keyword to declare a singleton object. All the members defined inside the object are treated as static members and can be accessed without creating an explicit instance. The astute reader might have noticed that the definition in Hello.scala is declared as the object Hello. That is because a single instance of main is needed for running the program.

A common use of the singleton object is for declaring constants. For example, add the following line above the Hello main method:

![](/Users/ryan/Documents/temp/images/media/image16.png){width="6.5in" height="0.5145833333333333in"}

Then access the constant with the following line inside the main method:

![](/Users/ryan/Documents/temp/images/media/image17.png){width="6.5in" height="0.50625in"}

Objects are commonly used to hold factory methods for creating classes. This pattern is so common that Scala declares a special method definition for this called apply. The apply method can be thought of like a default factory method that allows the object to be called like a method. For example, inside the Recipe.scala file add an object above the class definition:

![](/Users/ryan/Documents/temp/images/media/image18.png){width="6.5in" height="1.2284722222222222in"}

Then back in the Hello main, change the creation of Recipe to the following:

![](/Users/ryan/Documents/temp/images/media/image19.png){width="6.5in" height="1.0055555555555555in"}

What is interesting about the use of the Recipe object here is that no method had to be specified—apply was called by default.

An object is considered a companion object when it is declared in the same file as the class and shares the name and the package. Companion objects are used to hold the static definitions related to class but do not have any special relationship to a class.

**SECTION 5**

**Case Classes**

Case classes in Scala are classes on steroids. When the Scala compiler sees a case class, it automatically generates helpful boilerplate code to reduce the amount of code for common tasks. The only difference is the class definition has the keyword case before it:

![](/Users/ryan/Documents/temp/images/media/image20.png){width="6.5in" height="0.5902777777777778in"}

When we prefix a class with case, the following things happen:

-   Constructor parameters (such as name and age) are made immutable fields by default. Scala does this by prefixing all parameters with val automatically.

-   Equals, hashCode and toString are generated based on the constructor parameters.

-   A copy method is generated so we can easily create a modified copy of a class instance.

-   A default implementation is provided for serialization.

-   A companion object and the default apply factory method is created.

-   Pattern matching on the class is made possible. This is not covered in this introduction but is a very important reason to use case classes.

Because Person is defined as a case class it will be compiled into something like the following:

![](/Users/ryan/Documents/temp/images/media/image21.png){width="6.5in" height="1.4048611111111111in"}

Here object Person is the companion object for class Person.

The Person class can then be created without using the new keyword:

![](/Users/ryan/Documents/temp/images/media/image22.png){width="6.5in" height="0.43194444444444446in"}

We can also define additional apply methods inside classes and objects.

**SECTION 6**

**Traits**

Traits can be viewed as an interface that provides a default implementation of some of the methods (Java 8 added something similar with default methods on interfaces). In contrast to classes, traits may not have constructor parameters and are not instantiated directly like a class. They can be used similarly to an abstract class:

![](/Users/ryan/Documents/temp/images/media/image23.png){width="6.5in" height="2.077777777777778in"}

The JapaneseGreetings class extends the Greetings trait and implements the sayHello method.

Traits can also be used to provide methods and variables that are mixed into a class instead of being extended. Let's make this example more interesting by adding one more trait.

![](/Users/ryan/Documents/temp/images/media/image24.png){width="6.5in" height="3.004861111111111in"}

The GermanGreetings extends both Greetings and DefaultGreetings. The later is mixed-in to provide the default greetings behavior. Traits can also be mixed-in at the instance level:

![](/Users/ryan/Documents/temp/images/media/image25.png){width="6.5in" height="0.8381944444444445in"}

This particular instance of JapaneseGreetings will have both sayHello and defaultHello methods.

**SECTION 7**

**Functions**

Functions are similar to a method in Scala except that a function is attached to a class. Instead, functions are usually declared as an argument to another method, like what action should be taken when a service is called or a link is clicked on. The benefit of a function is that it allows functionality to be treated as a method argument, or code as data.

![](/Users/ryan/Documents/temp/images/media/image26.png){width="6.5in" height="3.74375in"}

![](/Users/ryan/Documents/temp/images/media/image27.png){width="6.5in" height="2.061111111111111in"}

Functions are also values that are assigned to variables, and functions also have types. Methods are not values. These function values can then be passed around like other variables. The following creates a function that finds the successor of any given parameter and assigns that function to the succ variable.

![](/Users/ryan/Documents/temp/images/media/image28.png){width="6.5in" height="1.1784722222222221in"}

Here, foo is the name of the parameter and what comes after =&gt; is the body of the function.

We can invoke this function like we invoke methods:

![](/Users/ryan/Documents/temp/images/media/image29.png){width="6.5in" height="0.4986111111111111in"}

We can also pass functions as a parameter to other functions and methods. In the following example, the succAndLog method takes two parameters, an integer value, and a function that takes a single Int, and returns an Int.

![](/Users/ryan/Documents/temp/images/media/image30.png){width="6.5in" height="1.7513888888888889in"}

**SECTION 8**

**Collections**

The Scala collections library is one of the most powerful features of the language. The library implements all the common data structures such as sequences, sets, and maps (also called dictionaries). Scala collections come in many forms—they can be immutable, mutable, and parallel. The language encourages you to use immutable collection APIs and imports them by default.\
Here is how collection types relate to each other:![](/Users/ryan/Documents/temp/images/media/image31.png){width="6.5in" height="4.6402777777777775in"}

Here are a few examples of how collection classes can be instantiated:

![](/Users/ryan/Documents/temp/images/media/image32.png){width="6.5in" height="2.1666666666666665in"}

Now let’s see how we can perform some common tasks using Scala collections.

//transform all the elements of the collection

![](/Users/ryan/Documents/temp/images/media/image33.png){width="6.5in" height="2.0229166666666667in"}

//filtering

![](/Users/ryan/Documents/temp/images/media/image34.png){width="6.5in" height="0.7215277777777778in"}

//grouping elements of collections based on the return value

![](/Users/ryan/Documents/temp/images/media/image35.png){width="6.5in" height="1.3215277777777779in"}

//sorting

![](/Users/ryan/Documents/temp/images/media/image36.png){width="6.5in" height="0.6895833333333333in"}

Scala provides mutable counterparts of all the immutable collections. For example, the following creates a mutable sequence of numbers:

![](/Users/ryan/Documents/temp/images/media/image37.png){width="6.5in" height="0.9298611111111111in"}

Here are some of the useful methods defined in the Traversable trait that are available to all collection types:

![](/Users/ryan/Documents/temp/images/media/image38.png){width="6.5in" height="6.026388888888889in"}

![](/Users/ryan/Documents/temp/images/media/image39.png){width="6.5in" height="2.0722222222222224in"}

![](/Users/ryan/Documents/temp/images/media/image40.png){width="6.5in" height="0.7736111111111111in"}

Scala provides another version of collection that evaluates elements in parallel. This is perfect for dividing work and taking advantage of available processing power of multi-core processors. The following example creates an instance of parallel seq collection and transforms each element in parallel.

![](/Users/ryan/Documents/temp/images/media/image41.png){width="6.5in" height="0.7972222222222223in"}

The map method of parallel collection tries to run the given function in parallel and evaluates each element in parallel:

![](/Users/ryan/Documents/temp/images/media/image42.png){width="6.5in" height="1.445138888888889in"}

Run the above code a few times to see how different threads are used for processing the map method.

**SECTION 9**

**Concurrency**

Concurrency is hard unless you have the right level of abstraction. The most common approach to solve concurrency problems is multi-threaded code with mutable states, which is very hard to maintain and reason about. And it makes it very difficult to find bugs because they only tend to show up under a large load. Scala takes a different approach to concurrency. Instead of threads, which are a very low level constructs, Scala provides developers with a higher level of abstraction with Futures and Promises. (Akka \[http://akka.io/\] also provides the Actor programming paradigm that is also a high-level abstraction for concurrent programming. See the Further Learning section for additional references.) This section will only explore Future.

Future is an object holding a value that may become available at some point. This value is usually the result of some other computation. A Future object is completed with either a value or an exception. Once it is completed it becomes in effect immutable—it can never be overwritten. The simplest way to create a Future object is to invoke the Future method, which starts an asynchronous computation and returns a Future holding the result of that computation. The result becomes available once the Future completes.

![](/Users/ryan/Documents/temp/images/media/image43.png){width="6.5in" height="1.1854166666666666in"}

The line import ExecutionContext.Implicits.global above makes the default global execution context available. An execution context is a thread pool that executes the tasks submitted to it. The future object uses this execution context to asynchronously execute the given task. In this case the task is someTimeConsumingComputation. The statement Future { … } is what actually starts Future running in the given execution context.

Once Future is completed, registering a callback can retrieve the value. A separate callback is registered for both the expected value and an exception to handle both possible outcome scenarios:

![](/Users/ryan/Documents/temp/images/media/image44.png){width="6.5in" height="1.1840277777777777in"}

following line will complete the future with exception:

![](/Users/ryan/Documents/temp/images/media/image45.png){width="6.5in" height="0.41944444444444445in"}

Futures are very handy tool to run multiple parallel computations and then compose them together to come up with a final result. The following example starts two asynchronous tasks and could run in parallel if there were enough CPU cores available:

![](/Users/ryan/Documents/temp/images/media/image46.png){width="6.5in" height="1.2305555555555556in"}

Scala’s for-expression can be used to compose (or combine) the results of multiple Future objects into a single result. In this example the Futures can be composed together to make a decision as to whether we should buy stocks in CHF. To do this we reference the futures inside the for {...} block and take the values that are returned from the future objects. Those values can then be used in the yield {...} block to check if the value is profitable. An important point to notice is the Future is created outside the for-expression and the for-expression is acting as a callback for when the Future completes. If the Future were created inside the for-expression then the second future will only be created when the first Future completes successfully.

![](/Users/ryan/Documents/temp/images/media/image47.png){width="6.5in" height="2.7423611111111112in"}

Finally, a callback is registered to retrieve the value of the isProfitable method.

![](/Users/ryan/Documents/temp/images/media/image48.png){width="6.5in" height="1.2375in"}

**SECTION 10**

**For-comprehensions**

A for-comprehension in Scala is like a Swiss Army knife: you can do many things with it using basic simple elements. The for expression in Scala consists of a for keyword followed by one or more enumerators surrounded by parentheses and an expression block or yield expression.

The following example adds all the elements of the first list with all the elements of the second list and creates a new list:

![](/Users/ryan/Documents/temp/images/media/image49.png){width="6.5in" height="2.3006944444444444in"}

![](/Users/ryan/Documents/temp/images/media/image50.png){width="6.5in" height="1.3020833333333333in"}

The if condition after a &lt;- aList is called a guard clause and it will filter out all the odd numbers and only invoke the aList generator for even numbers.

**SECTION 11**

**Build**

Scala can be built with a number of tools such as Gradle, Maven or even Ant. The most common way to build Scala however is sbt. The sbt build tool is used for managing dependencies, compiling the app, running the app, and running the tests. The primary build file is the build.sbt in the root of the project directory and then the project/build.properties file specifies the version of sbt to use along with the build properties. The primary build definition in the build.sbt file looks something like:

![](/Users/ryan/Documents/temp/images/media/image51.png){width="6.5in" height="1.3909722222222223in"}

The libraryDependencies section of the build.sbt defines the application dependencies, which should be available in a public Maven repository. You can also add your own Maven repository using the resolvers setting. The dependencies in libraryDependencies are a comma-separated list in the form:

![](/Users/ryan/Documents/temp/images/media/image52.png){width="6.5in" height="0.4270833333333333in"}

As an example, to add the jsoup driver add the following line:

![](/Users/ryan/Documents/temp/images/media/image53.png){width="6.5in" height="0.4270833333333333in"}

Sbt build also supports sub-projects so that you can partition your application into multiple smaller pieces. This can improve build times and make different pieces more easily reusable.

More information about sbt can be found on the sbt homepage (http://www.scala-sbt.org/).

**SECTION 12**

**Further Learning**

Coursera provides a free online Scala training course: <https://www.coursera.org/course/progfun>

Community-driven documentation for Scala can be found at: [http://docs.scala-lang.org](http://docs.scala-lang.org/)

Typesafe provides a number of Free E-Books at: <http://typesafe.com/resources/e-books>

Activator contains a number of other templates that will get you started learning about other aspects of Scala and the Typesafe Platform, like:

Atomic Scala Examples: <http://typesafe.com/activator/template/atomic-scala-examples>

An introduction to sbt: <http://typesafe.com/activator/template/hello-sbt>

Hello Akka!:

<http://typesafe.com/activator/template/hello-akka>

Hello Play!:

<http://typesafe.com/activator/template/hello-play>

For a full list of templates check out: <http://typesafe.com/activator/templates>

Twitter Scala School also provides a great Scala Introduction: <http://twitter.github.io/scala_school>
