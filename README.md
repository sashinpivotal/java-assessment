# Java Assessment Instruction

A few words before we start:

- You are going to perform the Java coding tasks as described below (with your screen shared) and answer related questions to your instructor.
  - Your instructor is not watching you every second. S/he is here to answer any logistics-related questions you might have.
  - You can let your instructor know when each time you are done with a task.)
- You are allowed to finish these tasks in 3 hour period but you are welcome to finish it earlier.

BTW, only the following topics are covered in this assessment:

- Data encapsulation, constructors
- Constructor and method overloading
- toString() and method overriding
- Basic java.time classes (LocalDate and Period)
- Enum types (simple)
- Basic boolean logic
- Throwing JDK-provided and custom exceptions,
  and handling them in client-side code

## Task 1.0: Create Maven project (skip this step if you already have done so)
- Create Java Maven project called "java-assessment"
  locally using IntelliJ
- Create GitHub repository with the same name
  with default values of all the other options
  - DO NOT select "Add a README file"
  - DO NOT add .gitignore file
- Sync up the local Maven project with the newly
  created GitHub repository
  - "git remote add origin <your-github-repo>"
  - "git branch -M main" (if your main branch is not "main")
  - "git push -u origin main"
- Provide the GitHub repository URL to the instructor
  before moving on


## Task 1.1: Create Person class
- Create package called "org.humanity"
- Write "Person" class, with the following two fields
  with proper access modifiers

```java
   String name;
   LocalDate birthDate;
```

- Write (or generate) getter methods for each 
  property (no setters need to be written or
  generated)

## Questions A
- As currently written, how many constructors does this class have?
- If the client code were written as below, what are the values 
  of "name" and "birthDate" fields?

```java
Person p1 = new Person();
```

- How will the client specify values for the "name" and "birthDate" 
  properties in a Person object if there are no setters?

## Task 1.2: Write a new constructor
- Write two argument constructor that takes "name" and "birthDate" 
  as arguments

## Task 1.3: Write "toString()" method
- Write (or generate via IDE) a toString() method.  If generating it, 
  change the generated code to use the getters 
  instead of direct field access. Also use 
  "getClass().getSimpleName()" for the classname, instead of 
  hardcoding it. 

## Questions B
- In the above task, would you use @Override annotation? 
  Explain why or why not?
- What is the parent class whose method is being overriden?

## Task 2.1: Write client code
- Create package "org.humanity.client" and in it, create 
  main-class "PersonClient".
- Create 3 instances of "Person" class, providing "name" and 
  "birthDate" values as constructor arguments, and call "toString()" 
  on each, printing the returned string from each call. Use
  the following as values of "name" and "birthDate".  

```
Jay      12/5/1966	(use p1 as variable name)
Kathryn	 7/26/1977	(use p2 as variable name)
Craig	 11/5/1950	(use p3 as variable name)
```

- Run the client code and explain the output
- Comment out the "toString()" method in the "Person" class
  and re-run the client code, explain the output
- Uncomment the "toString()" method

## Task 3.1: Write methods
- In the "Person" class, write two "eat()" methods: one "eat()"
  method should print a message like 
  "<name> is eating their favorite food." and 
  the other "eat(String favoriteFood)" method should be similar, 
  except that it also prints the name of the favorite food
  given as a method argument.
- Write client code that calls both of these methods using
  p1 (Jay) variable

## Questions C
- In the above task, you have created two methods with the 
  same name in the same class. What is that called?

## Task 4.1: Create enum
- Create enum called "Food", to represent a constrained 
  set of food items: SALAD, CHICKEN, PASTA, FISH, FRUIT, NUTS
- Refactor the "eat(String favoriteFood)" method to use the "Food"
  enum
  - Fix compile error in the PersonClient and run it
- Refactor the code so that the "eat(Food favoriteFood)" method  
  to format the output to use the lower case, i.e., 
  "<name> is eating salad" instead of "<name> is eating SALAD"?

## Task 5.1: Add a boolean field
- In the "Person" class, add boolean field called "isVegetarian"  
  and getter/setter methods for it (which can be generated).
- Include this property to the "toString()" method.
- Add another constructor for this new property, i.e., 
  a 3-argument constructor (name, birthDate, isVegetarian).
- Test-drive from client: make p2 (Kathryn) a vegetarian 
  by calling this new 3-argument constuctor.

## Questions D
- In p1 (Jay) and p3 (Craig), "isVegetarian" is "false".  Why?

## Task 6.1: Use JDK-provided exception
- (Background info)
  - If an instance of Person is vegetarian, they should not eat meat.  
    (Makes sense!) Are any of the foods specified in the Food 
    enum considered "meat?"  Yes – CHICKEN and FISH.
  - How should we handle the situation, in which a client calls 
    "eat(enum Food)" on a vegetarian Person, passing in a
    "meat" item? Yes, correct. You throw an exception.
- Refactor the "eat(Food)" method accordingly throwing 
  JDK-provided "IllegalArgumentException" to handle the case above.
- Did you have to catch "IllegalArgumentException" or uses
  "throws" clause on the method signature?  Why or why not?
- Writ client code that checks the above on p2 (Kathryn), 
  who is vegetarian as shown below

```java
	p2.eat(Food.SALAD);
	p2.eat(Food.CHICKEN);	// exception
	p2.eat(Food.NUTS);	// not reached
```
- Explain what happened
- Call the above "eat(..)" method to "p1" and "p3".
  Do you experience exceptions? Why not?

## Task 7.1: Create a custom exception
- We are now going to change "eat(Food favoriteFood)" to throw a
  custom (checked) exception.
- Write custom exception class called "VegetarianException" (checked) 
  exception with the 4 usual constructors.
- Change "eat(Food)" to throw "VegetarianException" instead of 
  "IllegalArgumentException" and handle compile errors accordingly
- Handle compiler error accordingly

## Questions E
- Why do you have to catch the "VegetarianException" exception or
  adds "throws" clause to the the method signature?

## Task 8.1: Use LocalDate and Period classes
- In the "Person" class, write "getAge()" method that returns
  the person's age in whole years (integer). 
  - This does not require any additional field, because the  
    person's age can be calculated.
  - Take a look at the Javadoc of "LocalDate" class and
    "Period" class if necessary
- Test-drive this in this client – write code to produce an
  output "\<name\> is \<age\> years old."

## Task 9: Push your code to your GitHub repo
- Commit all chagnes and push it to the GitHub repo

