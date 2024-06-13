# Appendix A: AL Syntax Reference

## A.1 Comprehensive Syntax Guide

Provide a detailed reference of AL syntax, covering keywords, operators, and data types.

### Keywords

- `var`
- `procedure`
- `begin`
- `end`
- `if`
- `then`
- `else`
- `repeat`
- `until`

### Operators

- `+` (Addition)
- `-` (Subtraction)
- `*` (Multiplication)
- `/` (Division)
- `=` (Equal to)
- `<>` (Not equal to)
- `<` (Less than)
- `>` (Greater than)
- `<=` (Less than or equal to)
- `>=` (Greater than or equal to)

### Data Types

- `Integer`
- `Decimal`
- `Boolean`
- `Text`
- `Date`
- `Record`

## A.2 Commonly Used Functions and Libraries

List commonly used AL functions and libraries with descriptions and examples.

### Message

Displays a message to the user.

Example:
```al
trigger OnAfterValidate()
var
    Item: Record Item;
begin
    Item.Reset();
    Item.SetRange("No.", Rec."Item No.");
    if item.FindFirst() then
        Message('Item found %1', Item.Name);
    else
        Message('Item not found %1');
```

### StrSubstNo 
Substitutes parameters into a string.
```al
Message(StrSubstNo('Total: %1', 2));
```

### Rec.FindFirst
Finds the first record in a table.

Example:
```al
trigger OnAfterValidate()
var
    Item: Record Item;
    ItemUOM: Record "Item Unit of Measure";
begin
    Item.Reset();
    Item.SetRange("No.", Rec."Item No.");
    if item.FindFirst() then begin
        ItemUOM.Reset();
        ItemUOM.SetRange("Item No.", Rec."Item No.");
        ItemUOM.SetRange(Code, Rec."Unit of Measure Code");
        if ItemUOM.FindFirst() then
            Rec.Validate("Unit Cost", item."Unit Cost" * ItemUOM."Qty. per Unit of Measure");
    end
    else
        Message('Item not found %1');
end;
```