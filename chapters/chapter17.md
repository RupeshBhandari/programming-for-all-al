# Chapter 17: Advanced AL Features
17.1 Working with AL Eventing
AL eventing allows you to extend and customize Business Central without modifying the base application. Use event publishers and subscribers to respond to specific events.

Example:

```al
codeunit 50103 EventSubscribers
{
    [EventSubscriber(ObjectType::Table, Database::Customer, 'OnBeforeInsertEvent', '', true, true)]
    local procedure HandleCustomerInsert(var Rec: Record Customer; RunTrigger: Boolean)
    begin
        if Rec.Name = '' then
            Error('Customer name cannot be empty.');
    end;
}
```

## 17.2 Leveraging the AL API
The AL API provides a set of functions and objects to interact with Business Central's core functionality. Use the API to create, read, update, and delete records.

Example:

```al
codeunit 50104 ALAPIUsage
{
    procedure GetCustomerBalance(CustomerNo: Code[20]): Decimal
    var
        Customer: Record Customer;
    begin
        if Customer.Get(CustomerNo) then
            exit(Customer."Balance (LCY)");
        else
            Error('Customer not found.');
    end;
}
```


## 17.3 Advanced AL Patterns and Techniques
Advanced patterns and techniques in AL include singleton patterns, dependency injection, and extension management.

Example:

```al

codeunit 50105 SingletonPattern
{
    SingleInstance = true;
    var
        instance: Codeunit 50105;
    
    procedure GetInstance(): Codeunit 50105
    begin
        if not assigned(instance) then
            instance := codeunit 50105;
        exit(instance);
    end;
}
```