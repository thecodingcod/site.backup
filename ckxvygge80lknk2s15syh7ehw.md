## The Essential Unit Testing Techniques, Part 1

Unit testing plays a vital role in the software development process, but how do we actually test our code? 

In the following article I'll try to summarize and mention various techniques followed by .NET Developer using the [NUnit](https://nunit.org/) library.


## Testing strings

Testing against specific strings is not a robust way of testing strings, For example

```csharp
Assert.That(result, Is.EqualTo("<strong>abc</strong>"));
```

👍 As a rule of thumb, testing strings is recommended to be more general than if it was too specific it would fail with every tiny change!

👍 Strings are all about format! so any method that can test the format for you is a viable testing method!

- Using string interpolation `$"{}"` or `string.Format()`
- Using `Does.StartWith`, `Does.EndWith`, `Does.Contain` methods provided by `NUnit`
- Using Regex (more advanced)

### 1. Using `$"{}"` format or `string.Format`

You can easily check the targeted format using `string.format` or `$"{}"` along with `Assert.That(result,Is.EqualTo())`, for example

```csharp
Assert.That(result, Is.EqualTo($"<strong>{str}</strong>"));
```

### 2. Using `Does.StartWith`, `Does.EndWith`, `Does.Contain` Methods

You can also use the fellow methods to check if a string is enclosed between specific words or tags!

```csharp
Assert.That(result, Does.StartWith("<strong>"));
Assert.That(result, Does.EndWith("</strong>"));
Assert.That(result, Does.Contain($"{str}"));
```

### 3. Using Regex

Regex is the god-level matching mechanism for strings! and fortunately, you can use it with `NUnit` to test your strings

```csharp
Assert.That(result, Does.Match("<pattern>"))
```

---

## Testing arrays and collections

Testing arrays or collections is a little bit tricky since there are many factors you can test

### 1. Testing if an Array has any elements

```csharp
Assert.That(result,Is.Not.Empty)
```

🔘 Yet, it's a general test case!

❓How can you make sure if it has a certain count of elements?

### 2. Testing the count of a collection

```csharp
 Assert.That(result.Count(),Is.EqualtTo(<num>))
```

🔘 It's also a general test case!

❓How can you make sure if it has a certain element?!

### 3. Testing if a collection contains X

```csharp
Assert.That(result, Does.Contain(1));
Assert.That(result, Does.Contain(3));
Assert.That(result, Does.Contain(5));
```

🤕 It brings more headache due to the repetitive work!

⚡ Fortunately, there is another way to do just the same!

```csharp
Assert.That(result, Is.EquivalentTo(new [] {1,2,3})
```

⁉️ What about the order of it's elements!

### 4. Testing the order of a collection

```csharp
Assert.That(result,Is.Ordered);
```

⁉️ And What about the uniqueness of its elements!

### 5. Testing the uniqueness of a collection's elements!

```csharp
Assert.That(result,Is.Unique);
```

---

## Testing Methods

Like arrays, there are also many factors that you consider when testing a method or a function!

- return type
- return value
- void methods
- exceptions are thrown by methods
- events being raised by a method
- private methods

### Testing return type

`NUnit` provides two different ways to test the return type of a method or a function.

1. `Is.TypeOf<>()`
2. `Is.InstanceOf<>()`

#### `Is.TypeOf<>()`

Checks if an instance (object or value) is of a specific type and just that type. for example:

```csharp
Assert.That(result,Is.TypeOf<NotFound>());
```

#### `Is.InstanceOf<>()`

Checks if an instance (object or value) is of a specific type or one of its derivatives. for example:

```csharp
Assert.That(result,Is.InstanceOf<NotFound>());
```

🗒️ It also provides the non-generic version of both methods, that can be used along with `typeof`

### Testing void methods (commands)

Void methods or commands are trickier to test than anything else because they 

1. change a state of an object either in memory, database
2. persist a state, they may store an object in a database or call a web service or a message queue.

Unfortunately, the only way to accomplish such a task is to preserve the state of the object being affected by that method. For example

```csharp
public class ErrorLogger
{
    public string LastError { get; set; }

    public event EventHandler<Guid> ErrorLogged; 
    
    public void Log(string error)
    {
        if (String.IsNullOrWhiteSpace(error))
            throw new ArgumentNullException();
            
        LastError = error; 
        
        // Write the log to a storage
        // ...

        ErrorLogged?.Invoke(this, Guid.NewGuid());
    }
}
```

```csharp
[Test]
[TestCase("Something went wrong")]
public void Log_WhenStringIsNotNullOrWhiteSpace_ThrowAnException(string message)
{
    _logger.Log(message);
    Assert.That(_logger.LastError,Is.EqualTo(message));
}
```

### Testing methods that throw an exception

`NUnit` provides a way to test if a method throws a specific exception and no matter it's a built-in exception or custom exception you can always test it!

But... you cannot just call your method in a normal way and expecting the Assert to detect that exception rather you've to call it as a delegate within the `Assert.That` method.

So, Instead of

```csharp
[Test]
[TestCase("")]
[TestCase(" ")]
[TestCase(null)]
public void Log_InvalidErrorMessage_ThrowArgumentNullException(string message)
{
    _logger.Log(message); // Execution will be stopped as a result for the exception and the test will fail!
    Assert.That(_logger.LastError,Throws.ArgumentNullException);
}
```

Do the following

```csharp
[Test]
[TestCase("")]
[TestCase(" ")]
[TestCase(null)]
public void Log_InvalidErrorMessage_ThrowArgumentNullException(string message)
{
    Assert.That(() =>
    {
        _logger.Log(message);
    },Throws.ArgumentNullException);
}
```

If you notice, I've used the `Throws.ArgumentNullException` property to assert the result and that is a built-in exception. 

❓What about the Custom Exceptions?

💬 Well, you can use the `Throws.Exception.TypeOf<>()` method just for that!

## Testing methods that raise an event

Testing events is nothing more than testing if it was raised for a specific scenario or not, so what we gonna really need is a simple indicator to answer our question. For Example

```csharp
public class ErrorLogger
{
    public string LastError { get; set; }

    public event EventHandler<Guid> ErrorLogged; 
    
    public void Log(string error)
    {
        if (String.IsNullOrWhiteSpace(error))
            throw new ArgumentNullException();
            
        LastError = error; 
        
        // Write the log to a storage
        // ...

        ErrorLogged?.Invoke(this, Guid.NewGuid());
    }
}
```

Here, our event will send an argument which is `Guid.NewGuid()` which we can assume to be the indicator that will tell us if it was raised or not.

```csharp
[Test]
[TestCase("Something went wrong")]
public void Log_ValidError_RaiseErrorLoggedEvent(string messge)
{
    // Arrange
    var id = Guid.Empty;
		
		// Subscribe to the event
    _logger.ErrorLogged += (sender, arg) => { id = arg; };

    // Act
    _logger.Log(messge);

    // Assert
    Assert.That(id, Is.Not.EqualTo(Guid.Empty));
}
```

- So, to test the event, we are going to subscribe to it first
- Assign the passed `Guid` to a local variable, that was previously initialized with a default value.
- Finally, we can assert that the `Id` is not the same as its default value! which means that event has already been raised and mutated the local variable.

### Testing private methods

⁉️ How to test the private or protected methods? 

💭 You shouldn't test private methods! we are only testing the API of a class (aka public members)

❔ Does it mean that we should test against Interfaces?

#### Reasons

- Private methods are participating to be an actual part of the implementation details of a class, which can be changed at anytime from one version to another. but public members would stay the same!
- Hence, if you tested against private members your tests will be coupled with implementation detail.

![Testing Private Methods](https://cdn.hashnode.com/res/hashnode/image/upload/v1641049421409/LzyRUACpi.png)

---

## Code Coverage

⁉️ How do we know if we have enough tests?

Well, you can make use of a code coverage tool that is mainly were designed to

- Scale your code
- Answer that question by telling what parts of our code that's not fully covered by tests

### Available Tools

- Visual Studio Enterprise Edition

- Resharper Ultimate, Dot Cover

  > Dot Cover is a unit test runner

- NCover

---

## Resources
- [Unit testing for C# developers, by Mosh Hamedani](https://www.udemy.com/course/unit-testing-csharp/)



