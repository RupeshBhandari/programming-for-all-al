# Chapter 6: Control Structures
## 6.1 Conditional Statements
Conditional statements control the flow of execution based on boolean expressions:

- If statements execute code blocks based on conditions.
- Case statements evaluate an expression against multiple values.

Example:
```al
// if else
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

// case
var
    score: Integer;
begin
    score := 85;
    case score of  
        1,2,9:  
            message('1, 2, or 9.');  
        10..100:  
            message('In the range from 10 to 100.');  
    else  
        message('Neither 1, 2, 9, nor in the range from 10 to 100.');  
end;
```

Note:
When you use a case statement, indent the value sets by four character spaces. If you've two or more value sets on the same line, then separate them by commas without spaces. The last value set on a line is immediately followed by a colon without a preceding space. The action starts on the line after the value set and is further indented by four character spaces. If there's a begin, then it should be put on a separate line unless it follows else. If a begin follows an else, then it should be on the same line as else. If there are more than two alternatives, use a case statement. Otherwise, use an if-then-else statement ([AL control statements](https://learn.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-al-control-statements)).


## 6.2 Looping Constructs
Loops allow repeated execution of code blocks:

- For loop iterates a specific number of times.
- While loop continues while a condition is true.
- Repeat-Until loop executes until a condition is true.

Example:
```al
// For loop
var
    i: Integer;
begin
    for i := 1 to 10 do begin
        Message('Iteration: %1', i);
    end;
end;

// while loop
var
    i: Integer;
begin
    while I < 1000 do begin
        I := I + 1;  
        message(format(I));
    end;
end;

// repeat until
var
    Count : Integer;
    Customer : Record Customer;  
begin
    if Customer.FindSet(true) then begin  
        repeat  
            if Customer.Name2 = '' then begin
                Customer.Name2 = Customer.Name;
                Customer.Modify();
            end;
        until Customer.Next() = 0;  
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

