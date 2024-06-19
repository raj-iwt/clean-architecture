# Clean Architecture


# SOLID Design Principles

Why we need single responsibility principle?

* To maintain the code for ease of use
* To test every corner of the code
* To be flexible and extendable
* To allow simultaneous development
* And more

## Single Reponsibility Principle

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

## Interface Segregation Principle

No client should be forced to depend on methods it does not use.



