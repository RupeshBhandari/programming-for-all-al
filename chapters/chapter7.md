# Chapter 7: Creating and Managing Tables

## 7.1 Defining Tables in AL

In AL, tables are defined to store and manage data. Each table consists of fields that hold specific pieces of information.

### Example Table Definition

```al
table 50100 Customer
{
    DataClassification = ToBeClassified;

    fields
    {
        field(1; "No."; Code[20])
        {
            DataClassification = CustomerContent;
        }
        field(2; Name; Text[100])
        {
            DataClassification = CustomerContent;
        }
        field(3; Address; Text[100])
        {
            DataClassification = ToBeClassified;
        }
        field(4; "Phone No."; Text[30])
        {
            DataClassification = ToBeClassified;
        }
    }

    keys
    {
        key(PK; "No.")
        {
            Clustered = true;
        }
    }
}
```

## 7.2 Primary Keys and Indexes

Primary keys uniquely identify records in a table. Indexes improve data retrieval performance.

### Defining Primary Keys

The primary key is defined in the `keys` section of the table definition.

```al
keys
{
    key(PK; "No.")
    {
        Clustered = true;
    }
}
```

### Defining Secondary Indexes

Secondary indexes can be defined to optimize queries on non-primary key fields.

```al
keys
{
    key(PK; "No.")
    {
        Clustered = true;
    }
    key(Name; Name)
    {
        Clustered = false;
    }
}
```

## 7.3 Field Data Types and Properties

AL supports various field data types. Each field can have properties that define its behavior and constraints.

### Common Data Types

- `Code[Length]`: Fixed-length alphanumeric code.
- `Text[Length]`: Variable-length text.
- `Integer`: Integer number.
- `Decimal`: Decimal number.
- `Date`: Date value.
- `Boolean`: Boolean value (true/false).

### Field Properties

- `DataClassification`: Defines the classification of the data for compliance purposes.
- `NotBlank`: Ensures the field cannot be empty.
- `TableRelation`: Defines a relationship to another table.

### Example with Properties

```al
field(1; "No."; Code[20])
{
    DataClassification = CustomerContent;
    NotBlank = true;
}
field(3; "Salesperson Code"; Code[10])
{
    TableRelation = Salesperson;
}
```

## 7.4 Relationships Between Tables

Relationships between tables are defined using the `TableRelation` property. This ensures referential integrity and allows for data lookups.

### Defining Table Relations

```al
field(2; "Customer No."; Code[20])
{
    TableRelation = Customer."No.";
}
```

## 7.5 Table Triggers
Table triggers in AL are special methods that automatically execute code at certain events during the lifecycle of a table record, such as when records are inserted, modified, or deleted.

### OnInsert Trigger
Executes code when a new record is inserted into the table. 

```al
trigger OnInsert()
begin
    // if the record is created without No then it auto assigns
    if "No." = '' then begin
            SalesSetup.Get();
            SalesSetup.TestField("Customer Nos.");
            NoSeriesMgt.InitSeries(SalesSetup."Customer Nos.", xRec."No. Series", 0D, "No.", "No. Series");
        end;
end;

```

### OnModify Trigger
Executes code when an existing record is modified.

```al
trigger OnModify()
    begin
        Error('No modification allowed')
    end;
```

### OnDelete Trigger
Executes code when a record is deleted from the table.

```al
trigger OnDelete()
begin
    // Code to execute when a record is deleted
    Error('Delete not allowed')
end;
```

### OnRename Trigger
Executes code when a record's primary key is changed.

```al
trigger OnRename()
begin
    // Code to execute when a record is renamed
    Message('A customer record has been renamed.');
end;
```


## 7.6 Best Practices for Table Design

- **Normalization**: Organize tables to reduce redundancy and dependency.
- **Naming Conventions**: Use clear and consistent naming conventions for tables and fields.
- **Data Integrity**: Define relationships and use field properties to ensure data integrity.
- **Performance**: Use indexes to optimize data retrieval and consider the impact on insert/update performance.

### Example of Best Practices

```al
table 50101 Order
{
    DataClassification = ToBeClassified;

    fields
    {
        field(1; "Order No."; Code[20])
        {
            DataClassification = OrderContent;
            NotBlank = true;
        }
        field(2; "Customer No."; Code[20])
        {
            DataClassification = CustomerContent;
            TableRelation = Customer."No.";
        }
        field(3; "Order Date"; Date)
        {
            DataClassification = ToBeClassified;
        }
    }

    keys
    {
        key(PK; "Order No.")
        {
            Clustered = true;
        }
        key(Customer; "Customer No.")
        {
            Clustered = false;
        }
    }
}
```