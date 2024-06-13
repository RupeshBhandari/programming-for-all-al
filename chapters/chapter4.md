# Chapter 4: Data Types and Variables in AL

## Primitive Data Types
AL supports various primitive data types, including:

- Integer: Whole numbers.
- Decimal: Numbers with fractional parts.
- Boolean: True/False values.
- Text: Strings of characters.
- DateTime: Dates and times.


##  Complex Data Types
In addition to primitive types, AL includes complex data types such as:

- Record: Represents a row in a table.
- Array: Collection of elements.
- Option: Enumerated types for predefined values.


## Variable Declaration and Initialization
Variables in AL are declared using the var keyword and can be initialized at the time of declaration. For example:
```al
var
    customerName: Text[100];
    totalAmount: Decimal;
begin
    customerName := 'John Doe';
    totalAmount := 1000.50;
end;
```