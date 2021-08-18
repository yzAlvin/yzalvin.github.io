
## What
The definition of an immutable:
> An object whose state cannot be changed after construction is called an immutable object

## Why 
* You know what to expect from an immutable
	Since the state of an immutable cannot change, we know what to expect from it. We know the state of the object is valid throught the object's lifetime.
	Nowhere in the code can the state be changed to potentially introduce inconsistencies that may lead to runtime errors.

* An immutable is a gate keeper for valid state
	An immutable object validates the state it is constructed with and only lets itself be instantiated if the state is valid. -> It is ALWAYS in a valid state.
	No need for null-checks or other validation strewn across the codebase. All the validations take place within the immutable object.

* Compilers love immutables
	Immutables are predictable, so compilers love them.
	Compilers can tell when a field that needs to be initialised, hasn't.
	The whole state of an immutable object has to be passed into the constructor, very handy when we add a new field to an existing object.

## How
Best practices

fields are **final** (java), **readonly** and **sealed** in c#.
This tells the compiler that their values must not change once initialised and that all field values are passed into the constructor.

```cs
class User
{
	private readonly int Id;
	private readonly string Name;
	User(int id, string name)
	{
		this.Id = id;
		this.Name = name;
	}
}
```

A Factory method for each valid combination of fields
An immutable object may have fields that are optional so that their value is null. 

Passing null into a constructor is a code smell, however, because we assume knowledge of the inner workings of the immutable. 

Instead, the immutable should provide a factory method for each valid combination of fields.

We can give names to the factory methods like newUser and existingUser, to make clear their intent.

```cs
class User
{
	private readonly int Id;
	private readonly string Name;
	
	private User(int id, string name)
	{
		this.Id = id;
		this.Name = name;
	}
	
	static User existingUser(int id, string name)
	{
		return new User(id, name);
	}

	static User newUser(string name)
	{
		return new User(null, name);
	}
}	
```

The `User` may have an empty Id because we somehow have to instatiate users that have not been saved to the database yet.

Instead of a single constructor into which we pass a `null` Id, we created a static factory method to which we only have to pass the name. Internally, the immutable then passes a null Id to the private constructor.

Make optional fields obvious
In the above example, id is optional and may be null.
To avoid potential NullPointerExceptions, make the getter return an Optional, so it could be null or an int.
Do not use optional itself as a field or argument type, because an optional itself may also be null.

Self-validate
To only allow valid state, an immutable may check within its constructor(s) if the passed-in values are valid according to the business rules of the class.

```cs
class User
{
	private readonly int Id;
	private readonly string Name;
	
	private User(int id, string name)
	{
		if (id < 0) throw new Exception("id must be >= 0"
		this.Id = id;
		this.Name = name;
	}
	
	# omit additional methods
}	
```

## Bad Practices
Don't use builders.

A builder is a class whose goal it is to make object instantiation easy. 
Instead of calling a constructor which takes all field values as arguments, we call fluid builder methods to set the state of an object step-by-step.

This is helpful if we have a lot of fields since its more readable than a call to a constructor with many parameters.

If we used a builder to create an immutable object, we are tricking the compiler that we're creating a valid object. The object instantiation will fail at runtime, or may not fail at all and we have an immutable with an unexpected null value.

Don't use withers.

"Wither" methods "change the state" of an immutable.
They are similar to setters, except that they usually start with the `with...` prefix.

This pattern works against the idea of an immutable, we're using an immutable as if it were mutable. If we see wither methods like this used on an imumtalbe, we should check if the class should rather be mutable because that's what the code implies.

They may be valid use cases for wither methods, but be skeptical.

Don't provide getters by default.
Even if you do not provide setters and make fields final, we could simply access something directly like a list via a getter and change its state.
If we *do* provide getters, we shuold make sure that the type of the field is also an immutable (like `int` or `string`) OR we should return a copy of the field instead of a reference to it.

# Use cases
* Concurrency
If we're working with concurrent threads that access the same objects, it's best if those objects are immutable. This way, we can not introduce any bugs that arise from accidentally modifying the state of an object in one of the threads.

In concurrency code, we should make objects mutable only if we have to.

* Value Objects
Value objects are objects that represent a certain value and not a certain entity. Thus, they have a value (which may consist of more than one field) and no identity.

An example of value objects are:
* wrappers of primitives like `long` and `Integer`
* a `Money` object representing a certain amount of money
* a `Name` object representing the name of a person

Since value objects represent a specific value, that value must not change. So, they must be immutable.

* Data Transfer Objects
When we need to transport data between systems or components that do not share the same data model. In this case, we can create a shared Data Transfer Object that is created from the data of the source component and then passed to the target component.

Although DTOs don't have to be immutable, it helps to keep the state of a DTO in a single place instead of scattered over the codebase.

Imagine we have a large DTO with tens of fields which are set and re-set over hundreds of lines of code, depending on certain conditions, before the DTO is sent over the line to a remote system. In case of an error, we'll have a hard time finding out where the value of a specific field came from.

If we make the DTO immutable instead, with dedicated factory methods for valid state combinations, there are only a few entry points for the state of the object, easing debugging and maintenance considerably.

* Domain Objects
Example: an object with an id that is loaded from the db, mainpulated for a certain use case, then stored back, usually within a db transaction.
A domain object is most certainly not immutable, but we will benefit from making it as immutable as possible. conditions, before the DTO is sent over the line to a remote system. In case of an error, we'll have a hard time finding out where the value of a specific field came from.

If we make the DTO immutable instead, with dedicated factory methods for valid state combinations, there are only a few entry points for the state of the object, easing debugging and maintenance considerably.

* Domain Objects
Example: an object with an id that is loaded from the db, mainpulated for a certain use case, then stored back, usually within a db transaction.
A domain object is most certainly not immutable, but we will benefit from making it as immutable as possible.
Making all fields final, so a bank account seems to be immutable at first glance. The deposit and withdraw methods manipulate the state however, so it's not immutable, but they provide very targeted entry points for manipulation that may even contain business rules.

We're making as many of the domain object's fields as possible immutable and provide focused manipulation methods if we cannot get around it.

* "Stateless" service objects
Even so-called "stateless" service objects usually have some kind of state.
Usually, a service has dependencies to components that provide database access for loading and updating data.
Make fields final and provide a matching constructor.

Conclusion

Every time we add a field to a class we should make it immutable by default. If there is a reason to make it mutable, that's fine, but unnecessary mutability increases the chance of introducing bugs and maintainability issues by unintentionally changing state.

[r1](https://reflectoring.io/java-immutables/)


