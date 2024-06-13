# Chapter 5: Operators and Expressions
## 5.1 Arithmetic Operators
AL includes standard arithmetic operators for performing mathematical calculations:

+ (addition)
- (subtraction)
* (multiplication)
/ (division)
Example:
```al
var
    total: Decimal;
    quantity: Integer;
    price: Decimal;
begin
    quantity := 10;
    price := 15.5;
    total := quantity * price; // total is 155.0
end;

```

## 5.2 Logical and Comparison Operators
Logical operators allow you to perform boolean logic operations, while comparison operators compare values:

Logical: AND, OR, NOT
Comparison: =, <>, <, >, <=, >=
Example:
```al
var
    isActive: Boolean;
    count: Integer;
begin
    isActive := TRUE;
    count := 5;
    if isActive AND (count > 0) then
        Message('The record is active and count is greater than zero.');
end;

```

## 5.3 Working with Expressions
Expressions in AL can combine operators and functions to compute values. They are used in assignments, conditions, and other contexts:
```al
var
    discountRate: Decimal;
    price: Decimal;
    finalPrice: Decimal;
begin
    discountRate := 0.1;
    price := 100;
    finalPrice := price * (1 - discountRate); // finalPrice is 90
end;

```