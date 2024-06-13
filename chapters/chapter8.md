# Chapter 8: Designing Pages and User Interfaces
## 8.1 Page Types and Properties
Pages define how data is presented to users. Common page types include:

- Card: Displays details of a single record.
- List: Shows multiple records in a grid.
- Document: Used for transactional data entry.
Example:

```al
page 50100 CustomerCard
{
    PageType = Card;
    SourceTable = Customer;
    layout
    {
        area(content)
        {
            group(Group)
            {
                field("No."; "No.")
                {
                    ApplicationArea = All;
                }
                field("Name"; "Name")
                {
                    ApplicationArea = All;
                }
            }
        }
    }
}
```

## 8.2 Creating and Customizing Pages
Creating a page involves defining its layout and specifying the source table. Customization includes adding fields, groups, and actions to enhance functionality.

Example:

```al
pageextension 50101 CustomerCardExtension extends "Customer Card"
{
    layout
    {
        addlast(Content)
        {
            group(AdditionalInfo)
            {
                field("Phone No."; "Phone No.")
                {
                    ApplicationArea = All;
                }
            }
        }
    }
}
```

## 8.3 Page Actions and Events
Actions and events add interactivity to pages. Actions are buttons that trigger AL code, while events allow you to respond to user interactions.

Example:

```al
pageextension 50102 CustomerListExtension extends "Customer List"
{
    actions
    {
        addfirst(Processing)
        {
            action(PrintCustomer)
            {
                ApplicationArea = All;
                Caption = 'Print Customer';
                Image = Print;
                trigger OnAction()
                begin
                    // AL code to print customer details
                end;
            }
        }
    }
}
```