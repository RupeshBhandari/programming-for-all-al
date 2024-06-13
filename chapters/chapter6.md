# Chapter 6: Control Structures
## 6.1 Conditional Statements
Conditional statements control the flow of execution based on boolean expressions:

If statements execute code blocks based on conditions.
Case statements evaluate an expression against multiple values.
Example:
```al
var
    score: Integer;
begin
    score := 85;
    if score >= 90 then
        Message('Grade: A')
    else if score >= 80 then
        Message('Grade: B')
    else
        Message('Grade: C');
end;
```
## 6.2 Looping Constructs
Loops allow repeated execution of code blocks:

For loop iterates a specific number of times.
While loop continues while a condition is true.
Repeat-Until loop executes until a condition is true.
Example:
```al
var
    i: Integer;
begin
    for i := 1 to 10 do begin
        Message('Iteration: %1', i);
    end;
end;

```

## 6.3 Error Handling and Assertions
Error handling ensures your program can handle unexpected situations gracefully:

AssertError triggers an error when a condition fails.
Error raises an error with a custom message.
Example:
```al
var
    divisor: Integer;
begin
    divisor := 0;
    if divisor = 0 then
        Error('Division by zero is not allowed.');
end;

```

