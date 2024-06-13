# Chapter 10: Reports and Data Analysis
## 10.1 Creating Reports
Reports are used to present data in a structured format. They consist of data items (tables) and layout (design). AL allows you to define the data structure and the layout using RDLC or Word.

Example:

```al
report 50100 CustomerReport
{
    DataItems
    {
        dataitem(Customer; Customer)
        {
            DataItemTableView = SORTING(Name);
        }
    }
    layout
    {
        // RDLC or Word layout
    }
}
```

## 10.2 Working with Report Data Items
Data items define the tables and relationships for the report. You can filter and sort data to customize the report's output.

Example:

```al
report 50101 SalesReport
{
    DataItems
    {
        dataitem(SalesHeader; "Sales Header")
        {
            DataItemTableView = SORTING("No.");
            dataitem(SalesLine; "Sales Line")
            {
                DataItemLink = "Document No.=FIELD(No.)";
            }
        }
    }
    layout
    {
        // RDLC or Word layout
    }
}
```

## 10.3 Customizing Report Layouts
Customizing layouts involves defining the visual representation of the report. You can use Visual Studio or Word to design the layout.

Example:

```al
reportextension 50102 CustomSalesReport extends "Standard Sales Report"
{
    layout
    {
        // Custom layout design
    }
}
```