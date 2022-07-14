[[_TOC_]]
# Software-Pet-Store
The class exercise repository for the software 1 and 2 tracks.  Look at the list of branches to find the solution for each weeks exercise.

# Software 1 - Class Exercise 3: Pet Store Part 1
## Goals
- Create the base classes for the store.
- Interact with the classes by making some objects and running basic logic on them.
- Learn how to make a console app wait for certain input before exiting using a loop.

## Instructions
1. Create a new console app in Visual Studio.  Make sure to give the solution a good name and make sure you create the solution in place that you can find it later.
2. Add a class to your project called `Product`.  This class will be what's called a _base_ class or a _parent_ class.  This will be the most basic class that all product classes will inherit from.
3. Add the following _properties_ to your naew class.
  - Price - Type `decimal`
  - Name - Type `string`
  - Quantity - Type `int`
  - Description - Type `string`
4. Add another class called `CatFood`.  Make this class _inherit_ from the base class `Product`.
5. Give `CatFood` a few _Properties_.
  - WeightPounds - Type `double`
  - KittenFood- Type `bool`
6. Make another class called `DogLeash` and have it inherit from `Product` as well. Give it a the following _Properties_ 
  - LengthInches - Type `int`
  - Material - Type `string`
7. Back in your `Program` file.  Create an _Instance_ of `CatFood` and `DogLeash`.  This is where you use the `new` keyword.
8. Once you've created an instance of each class, assign values to their properties.
9. After the objects have some data in them, use an `if else` statment to conditionally print something to the console.  For example, if my cat food bag weighs more that 10lbs, print "heavy bag" to the console, but if it's less than 10lbs, print "small bag".
10. Now we want to get this conaole app to run until the user decides to end it.  We will do this by using a `while` loop.  Loops require 3 things: an inital condition, check in condition, and a change in condition.  Our inital condition is going to be our first input from the user.  Our check is what is in the while loop.  Our change is going to be what the user inputs after an action has been complete.  So, let's get started with the initial condion.
11. Above the code you wrote in 7 - 9, add the following lines: `Console.WriteLine("Press 1 to add a product");` and below that add `Console.WriteLine("Type 'exit' to quit");`.
12. Add this line of code below what you added in step 11 `string userInput = Console.ReadLine();`.  This will get what the user enters before hitting enter.
13. Now add your while loop.  The condition in the loop should be something like this: `userInput.ToLower() != "exit"`.  We use the method `ToLower` just in case the user enters "Exit" instead of "exit".
14. Inside the brackets for the while loop, at the end, add this line `userInput = Console.ReadLine();`.  This is our change in condition.  We will add code before this though, so it will make more sense after that.