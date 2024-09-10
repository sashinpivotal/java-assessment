

## Task 1.0: Create Maven project
- Create Java Maven project called "java-assessment"
  locally using IntelliJ
- Create GitHub respository with the same name
- Sync up the local Maven project with the newly
  created GitHub repository
- Provide the GitHub repository URL to the instructor
  before moving on


## Task 1.1: Create Person class
- Create package called "org.humanity"
- Create class "Person", with the following two fields
  with proper access modifiers

```java
   String name;
   LocalDate birthDate;
```

- Write (or generate) getter methods for each 
  property (no setters need to be written or
  generated)

## Questions
- As currently written, how many constructors does this class have?
- If the client code were written as below, what are the values 
  of "name" and "birthDate"?

```java
Person p1 = new Person();
```

- How will the client specify values for the "name" and "birthDate" 
  properties in a Person object if there are no setters 
  and only this no-arg constructor?

## Task 1.2: Write a new constructor
- Write two argument constructor that takes "name" and "birthDate" 
  values

## Task 1.3: Write "toString()" method
- Write (or generate) a toString() method.  If generating it, 
  they should change the generated code to use the getters 
  instead of direct field access. They should also use 
  getClass().getSimpleName() for the classname, instead of 
  hardcoding it.  Step in and explain this last bit, if necessary.

## Questions
- In the above task, would you use @Override annotation? 
  Explain why or why not?
- What is the parent class whose method is being overriden?

## Task 2.1: Write client code
- Create package "org.humanity.client" and in it, create 
  main-class "PersonClient".
- Create 3 instances of "Person" class, providing "name" and 
  "birthDate" as constructor arguments, and call "toString()" 
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

## Task 3.1: Write new methods
- In the "Person" class, write two "eat()" methods: one "eat()"
  method  should print a message like 
  "<name> is eating their favorite food." and 
  the other method "eat(String favoriteFood)" should be similar, 
  except that it also prints the name of the food specified.
- Write client code that calls both of these methods

## Questions
- What is this called, when you have two methods with the 
  same name in the same class?

## Task 4.1: Create enum
- Create enum called "Food", to represent a constrained 
  set of food items: SALAD, CHICKEN, PASTA, FISH, FRUIT, NUTS
- Refactor the "eat(String favoriteFood)" to use the "Food"
  enum
- Refactor the code so that the "eat(Food)" method to format 
  the output, so that it reads more naturally, i.e., 
  "<name> is eating salad" instead of "<name> is eating SALAD"?

## Task 5.1: Add a boolean field
- In the "Person" class, add field "isVegetarian" and 
  getter/setter methods for it (which can be generated).
  did good w/boolean vegetarian field
- Include this property in the "toString()" method.
- Add another constructor for this new property, i.e., 
  a 3-argument constructor (name, birthDate, isVegetarian).
- Test-drive from client: make p2 (Kathryn) a vegetarian 
  by calling this new 3-argument constuctor.

## Questions
- In p1 (Jay) and p3 (Craig), "isVegetarian" is "false".  Why?

## Task 6.1: Use JDK-provided exception
- If an instance of Person is vegetarian, they should not eat meat.  
  Makes sense! Are any of the foods specified in the Food 
  enum considered "meat?"  Yes – CHICKEN and FISH.
- How should we handle this situation, when a client calls 
  "eat(enum Food)" on a vegetarian Person, passing in a "meat" item?
- Refactor the "eat(Food)" method accordingly throwing 
  "IllegalArgumentException" to handle the case above.
- Did you have to catch "IllegalArgumentException" or uses
  "throws" clause on the method signature?  Why or why not?
- Write test client code that checks the above on p2 (Kathryn), 
  who is vegetarian

```java
	p2.eat(Food.SALAD);
	p2.eat(Food.CHICKEN);	// exception
	p2.eat(Food.NUTS);	// not reached
```
- Call the above "eat(..)" methods to "p1" and "p3".
  Do you experience exceptions? Why not?

## Task 7.1: Create a custom exception
- We are now going to change eat(Food) to throw a custom (checked) exception.
- Write custom exception class called "VegetarianException" (checked) 
  exception with the 4 usual constructors.
- Change "eat(Food)" to throw "VegetarianException" instead of 
  "IllegalArgumentException" and handle compile errors accordingly

## Questions
- Why do you have to catch the "VegetarianException" exception or
  adds "throws" clause to the the method signature?

## Task 8.1: Use LocalDate and Period classes
- In the "Person" class, write "getAge()" method that returns
  the person's age in whole years (integer). 
  - This does not require any additional fields, the result 
    can be calculated.
  - Take a look at the Javadoc of "LocalDate" class and
    "Period" class
- Test-drive this in this client – write code to produce an
  output "<name> is <age> years old."

## Task 9.1: Use collection object
- Add support for food allergies – create custom checked exception 
  class called "FoodAllergyException", and add the following to 
  the "Person" class:

```java
    private Set<Food> allergyCausingFoods = new HashSet<>();          // Question: why use Set here?
	
	public void addFoodAllergy(Food food) {
      allergyCausingFoods.add(food);
	}
	
	public void eat(Food food) throws FoodAllergyException {
        
        // existing code
      
        // new code
        if (allergyCausingFoods.contains(food)) {
            throw new FoodAllergyException(getName() + " is allergic to " + food);
        }
    }
```

- Write client code that tests the above logic
