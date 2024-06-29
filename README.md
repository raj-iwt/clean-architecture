# Clean Architecture

## Separation of Concerns (SoC)

The idea is to separate the project or solution into logical blocks representing specific concern or aspect of the software.

**Benefits**
1. Maintainability
2. Modularity
3. Understandability

**Examples**

* Security and logging are cross-cutting concerns.
* Rendering a user interface is a concern.
* Handling an HTTP request is a concern.
* Copying an object into another is a concern.
* Orchestrating a distributed workflow is a concern.

## Don't repeat yourself (DRY)

The idea is that each block of code or concern should have a single, unambiguous representation within the project or system.

**Benefits**

1. Eliminate redundancy

```
public class Admin
{
    public async Task DisplayListAsync(
        IBookService bookService,
        IBookPresenter presenter)
    {
        var books = await bookService.FindAllAsync();
        foreach (var book in books)
        {
            await presenter.DisplayAsync(book);
        }
    }
}
public class Public
{
    public async Task DisplayAsync(
        IBookService bookService,
        IBookPresenter presenter)
    {
        var books = await bookService.FindAllAsync();
        foreach (var book in books)
        {
            await presenter.DisplayAsync(book);
        }
    }
}

```

The above two classes provides same function exept different class and method name. When you see duplication of code, encapsulate and refactor to reuse the logic.

```
public class Public
{
    public async Task DisplayAsync(
        IBookService bookService,
        IBookPresenter presenter)
    {
        var books = await bookService.FindAllAsync();
        foreach (var book in books)
        {
            await presenter.DisplayAsync(book);
        }
    }
}

public class AdminApp : Public
{
    // Additional admin functionalities
}
```

Additionally, we can encapsulate the IBookPresenter with books list instead passing the book so that we can pass different presenter implentation for different role.

## Keep it simple, stupid (KISS)

The idea is simplicity because more moving pieces mean breaks something. 

**Example**
1. Complex object hierarchy

## SOLID Design Principles

Why we need single responsibility principle?

* To maintain the code for ease of use
* To test every corner of the code
* To be flexible and extendable
* To allow simultaneous development
* And more

### Single Reponsibility Principle

Each class and module should focus on a single task at a time and all members are related to single purpose.

```
public interface IUser 
{
    bool Login(string username, string password);
    bool Register(string username, string password);
    void Logout();
    void LogError(string error);  // Irrelevant to IUser
    void SendEmail(string email); // Irrelevant to IUser
}
```

In the above interface, LogError and SendEmail method are irrelevant to IUser interface. We need to create new interface for Logging and Emailing separately.

### Interface Segregation Principle

No client should be forced to depend on methods it does not use.



