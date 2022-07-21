
# Software-Pet-Store
The class exercise repository for the software 1 and 2 tracks.  Look at the list of branches to find the solution for each weeks exercise.

The first excercises will contain a lot of information on what to do. As the exercises go on though, there will be less information and you will be required to do research if you don't understand what to do.

# Software 1 - Class Exercise 2: Pet Store Part 1
## Goals
- Create the base classes for the store.
- Interact with the classes by making some objects and running basic logic on them.
- Learn how to make a console app wait for certain input before exiting using a loop.

## Instructions
1. Create a new console app in Visual Studio.  Make sure to give the solution a good name and make sure you create the solution in place that you can find it later.
1. Add a class to your project called `Product`.  This class will be what's called a _base_ class or a _parent_ class.  This will be the most basic class that all product classes will inherit from.
1. Add the following _properties_ to your naew class.
   - Name - Type `string`
   - Price - Type `decimal`
   - Quantity - Type `int`
   - Description - Type `string`
1. Add another class called `CatFood`.  Make this class _inherit_ from the base class `Product`.
1. Give `CatFood` a few _Properties_.
   - WeightPounds - Type `double`
   - KittenFood- Type `bool`
1. Make another class called `DogLeash` and have it inherit from `Product` as well. Give it a the following _Properties_ 
   - LengthInches - Type `int`
   - Material - Type `string`
1. Now we want to get this conaole app to run until the user decides to end it.  We will do this by using a `while` loop.  Loops require 3 things: an inital condition, check in condition, and a change in condition.  Our inital condition is going to be our first input from the user.  Our check is what is in the while loop.  Our change is going to be what the user inputs after an action has been complete.  So, let's get started with the initial condion.
1. At the top of the files, add the following lines: `Console.WriteLine("Press 1 to add a product");` and below that add `Console.WriteLine("Type 'exit' to quit");`.
1. Add this line of code below what you added in step 11 `string userInput = Console.ReadLine();`.  This will get what the user enters before hitting enter.
1. Now add your while loop.  The condition in the loop should be something like this: `userInput.ToLower() != "exit"`.  We use the method `ToLower` just in case the user enters "Exit" instead of "exit".
1. Inside the brackets for the while loop, at the end, add this line `userInput = Console.ReadLine();`. This is our change in condition.  We will add code before this though, so it will make more sense after that. Add the instructions for the console app above that line again: `Console.WriteLine("Press 1 to add a product");` and `Console.WriteLine("Type 'exit' to quit");`. 
1. Inside of the while loop, above the what you added in the previous step, add an `if` statement.  This if statment will check the input of the user a second time to see if they wanted to add a product. We told them to enter "1" to add a product, so check for that in the if statment.  Remember, the input is a `string` type, not an `int`.
1. Create a new object.  It should be `CatFood` or `DogLeash` not the base class `Product`.  Note: remember to add a `using` statment so that the `Program` class knows where to find your class.
1. Since we don't really have a database, when we add a product, we're going to just create that object and print it to the console.  Use `Console.Write()` and `Console.ReadLine()` to get data from the user and then add it to the object you just created.  Since some of the types aren't going to match, you will need to convert them using the target types `Parse` method.  So to turn a string to an int, use `int.Parse()`.
1. To make printing the object easier, we'll use the `JsonSerializer` class.  You don't need to know all the ins and outs of how this works right now, but basically it will just convert our object to a json object.  Add the following line to your code: `Console.WriteLine(JsonSerializer.Serialize(dogLeash));`.  You will replace `dogLeash` with whatever you named your object.
1. Now, all you have to do is test it!  Run the application and see if everything works properly.

# Software 1 - Class Exercise 3: Pet Store Part 2
## Goals
- Learn how to use the 2 most commonly used collections: List and Dictionary.

## Instructions
In the last exercise we added a function to add a product to store. I this exercise, we're going to expand on that as well as add a new function to view our product list.

1. We're going to add a new class to handle all of our product functionality.  Add a new class called `ProductLogic`. 
1. In this class, add a new _private_ variable called "products" of type `List<Product>`.  Remember to add an underscore `_` before the name because it's a private variable.
1. Create a constructor for the class and in that constructor, create a new instance of the list class.  It should look something `_products = new List<Product>();`
1. Create a new function/method called `AddProduct`.  It should have no return type (so it'll return `void`) and accept one _argument_ called "product" and it should be of type `Product`. So the method will look like this: `public void AddProduct(Product product)`
1. In that method, use the `_product` variables `Add` method to add the method's argument to the private list.
1. Next create another method called `GetAllProducts`. The method's return type will be `List<Product>` and will have no arguments.  This method will be really simple, all you have to do is return our private variable: `return _products`.
1. Back in our main "Program" class, we're going to create an _instance_ of our new `ProductLogic`.  Make it a variable at the top of the file under the `using` statments. `var productLogic = new ProductLogic();`
1. Replace the line where we are serializing the product that the user is creating with the `AddProduct()` method and pass the product the user created into the method.
1. After adding the product, add a nice message below it to let the user know that the product was added.
1. Our next major thing to add will be some dictionaries to hold our specific types of products.  So back in `ProductLogic`, add 2 more private variables.  The first will be of type `Dictionary<string, DogLeash>` and the second will be `Dictionary<string, CatFood>`.  The `string` is the key and `DogLeash`/`CatFood` are the types of objects being stored in the Dictionary.  I'll let you choose some names for these variables.
1. Now, in `AddProduct` add an if statement. It's condition will check for the _Type_ of object. If it's a `DogLeash` it will be added to the dog leash dictionary.  If it's a `CatFood` object, it will be added to the cat food dictionary.  The key will be the product's name value.  So an if statement will look like this: `if (product is DogLeash)`.
1. Inside of this if statement, use the correct dictionaries `Add` method to add the product to it.  Note: you will probably have to convert the product to the correct child class using the `as` keyword.  That would look like this: `product as DogLeash`.
1. Add another if block that does the same thing except for `CatFood` instead of `DogLeash`.
1. Add another method called `GetDogLeashByName` it will have a return type of DogLeash and will have one argument of type `string` called "name".
1. This method will use the indexing brackets `[]` to use the name key being passed in to return the object with that key in the dictionary. That would look like something this: `return _dogLeash[name]`.
1. Back in the program class, add a new option for the user.  It will be option number 2 and will let them get a specific object out of the list.  Since they're only adding a dog leash right now, we're going to just let them view a dog leash as well. Use option number 1 as a template for what you need to do right now and only use the soultion when you get stuck.
1. All you have left to do now is test your program to make sure it's working!

# Software 1 - Class Exercise 4: Pet Store Part 3
## Goals
- Learn how to handle exceptions
- Implement some OOP principles in your program.

## Instructions
### Error Handling
1. Run your program and add a product.  Now use option 2 to get a product that doesn't exist.  The program should have thrown an error and completely stopped.  You generally don't want these kinds of things happening so let's add some error handling to our program.
1. In the `ProductLogic` class in the `GetDogLeashByName` method, _wrap_ `return _dogLeash[name];` with a `try` block. Wrap is a pretty common term that means basically "put inside of the curly braces".  
1. After the try block, add a `catch` block.  The catch keyword takes one argument and that has to be an Exception.  This is a pretty standard way of writing a catch: `catch(Exception ex)`.  What you do inside of the catch block is really up to you and dependent on the situation.  In ours, let's just return `null` and account for that in the class that uses the method.
1. Back in our Program file, check the result of `GetDogLeashByName` to see if it's `null` using an `if`/`else` statment. If it _is_ `null`, write a message saying that the product couldn't be found.  If it _isn't_ `null` have the program do what it was doing before.

### OOP Principles
You will need to work together with someone on this part, so find one or two people close to you
OOP Principles:
- encapsulation
- abstraction
- inheritance
- polymorphism

1. We'll first look at encapsulation.  In our program we've encapsulated our product specific logic in our `ProductLogic` class. Talk with someone else about why you think this could be helpful as the program gets larger.  It is totally okay to look it up on the internet!
1. Next is abstraction.  Abstraction will be expanded on much more in next weeks exercise, but for now discuss with someone what it means and how think it might be used in the future in the Pet Store application.
1. Inheritence is something you've already used.  It is easier to understand using the "is-a" terminology.  So Cat Food _is a_ product.  A dog leash _is a_ product.  Let's take this one step further and add one more level of _is-a_.  Add a new class called `DryCatFood` and have it inherit from `CatFood`.  Let's move the Weight property over to this new class since that would belong more in the dry cat food than it would in something like canned cat food.
1. Polymorphism was used in the `AddProduct` function.  Discuss with someone how this is using the polymorphism principle.

# Software 1 - Class Exercise 5: Pet Store Part 4
## Goals
- Add interfaces
- Use linq queries

## Instructions
### Interfaces
Interfaces are critical to modern programming.  There are multiple concepts and programming patterns that rely on interfaces.  While we aren't going to explore any of those in this course, we are going to learn how to use interfaces.
1. We have an existing class that would be great to have an interface for: `ProductLogic`.
1. Create a new _Interface_ and call it `IProductLogic`.  You do it the same way you do a class, you just select Interface isntead of Class.  If you create a class by accident, you can just change the keyword `class` to `interface`.
1. In this interface, we're going to be saying _what_ functions need to be implemented, not _how_ they are.
1. So look at the `ProductLogic` class and add the already existing methods to the interface.  Here's the first one: `public void AddProduct(Product product);`
1. Once all the existing methods have been added to the interface, head over to the `ProductLogic` class again and let's have the class _implement_ the interface.  You do this using the same syntax you use to have a class _inherit_ from another `:`.
1. Once we have `ProductLogic implementing `IProductLogic`, let's add a new method to our interface.
1. Add a method called `GetOnlyInStockProducts`.  It doesn't need to take any arguments and it will return `List<Product>`.
1. Heading back to `ProductLogic` you should see a build error.  This is because our `ProductLogic` class isn't fully implementing the interface.  We'll be doing that in the next section.

### Using Linq
1. In the `ProductLogic` class, in the constructor where you are creating a new list of products, instead of having that list be empty, go ahead and add 2 or 3 products to it.  One of those products should have a quantity of 0.
1. Add the method from the interface that hasn't yet been implemented.
1. In that method body, we are going to filter our product list to only return products with quantity greater than 0.
1. To normally do this, we would probably use a `for` loop to iterate through the whole list checking each one to see if its quantity is greater than 0.  If it is, we would add it to a new list then return that list.  We're going to use linq for this though which will greatly simplify our method.
1. In the method body, type of this: `return _products.Where(x => x.Quantity > 0).ToList();`
1. Let's take this a step further.  Let's say we would only want to return the names of the products.  We would do this by using the `Select` method.  This one would sit between `Where` and `ToList`. Go ahead and add `.Select(x=>x.Name)`.  You will have build errors from this, so go ahead and fix that.  You'll need to make changes in `ProductLogic` and `IProductLogic`.
1. Finally, add a UI option to view in stock products only.

# Software 1 - Class Exercise 6: Pet Store Part 5
## Goals
- Use an extension method to add functionality to a class you wouldn't normally have access to.

## Instructions
We're going to extend `List` to check for in stock items.  This is a check that we would potentially do a lot in the future of our program.  So adding a method to do this will make the code more readable and easier to maintain.
1. Create a new `static` class.  Call it `ListExtensions`.
1. In this class we're going to create a static method.  This one will be kind of complicated, so here's the method _signature_: `public static List<T> InStock<T>(this List<T> list) where T: Product`. 
1. Your mentors should have explained a little bit about _generics_.  They're not critical to understanding extension methods, but hopefully it will take some of the mystery out of how the method is working.  You'll learn much more about generics in the next course.
1. In the method body, return the "in stock" code we wrote last time.  Since this method is returning a list, remember to add the `ToList` at the end.
1. We can now use this new method in our `ProductLogic` class.  Go replace the "in stock" logic with this new method.
1. Add a new method (don't forget the interface) called `GetTotalPriceOfInventory`.  It will return a decimal.  Use your new `InStock` method, the `Select` method, and the `Sum` method to get your result.
1. Add a new UI option for the new method.
1. Now just test to make sure it works correctly.

# Software 1 - Class Exercise 7: Pet Store Part 6
## Goals
- Reafactor code to take advantage of "Clean Coding" principles you've learned.

## Instructions
This exercise won't have the usual format where there are detailed instructions.  Instead, it will simply provide some suggestions to make the application easier to maintain, extened, and read.
- Try finding duplicate code and moving them to methods.
- Is having everything in the program file the easiest to read?  Probably not, maybe try moving some stuff around into a new `UILogic` class or something like that.
- Add some class comments.  You can get them easily generated for you by adding `///` above a class, property, or method.
- Organize your files in the solution.  Add some folders to put classes in.  Don't forget to adjust the namespace to reflect it's new location in the solution.
- Wherever you can, use interfaces instead of concrete classes.  Some easy examples would be `IList`, `IDictionary`, and `IProductLogic`.
- Discuss with someone and try to figure out if you all were using any clean coding principles in the past exercises.