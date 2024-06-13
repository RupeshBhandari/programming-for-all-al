# Chapter 12: Integration with Other Systems
## 12.1 Using Web Services
Web services allow you to expose Business Central data and operations to external systems. AL supports both SOAP and OData web services.

Example:

```al
codeunit 50100 CustomerWebService
{
    [ServiceEnabled]
    procedure GetCustomer(var Customer: Record Customer)
    begin
        // Code to fetch customer data
    end;
}
```

## 12.2 Integrating with External APIs
AL can interact with external APIs using HTTP requests. This allows seamless integration with other applications and services.

Example:

```al
procedure CallExternalAPI()
var
    HttpClient: HttpClient;
    HttpResponseMessage: HttpResponseMessage;
    JsonResponse: Text;
begin
    HttpClient.Get('https://api.example.com/data', HttpResponseMessage);
    if HttpResponseMessage.IsSuccessStatusCode then begin
        HttpResponseMessage.Content.ReadAs(JsonResponse);
        Message('Response: %1', JsonResponse);
    end else
        Error('Failed to call API');
end;
```

### 12.3 Data Exchange and Interoperability
Data exchange features in Business Central include XMLports and Data Exchange Definitions, enabling import/export of data in various formats.

Example:

```al
xmlport 50100 CustomerImport
{
    Schema
    {
        // Define XML schema for import
    }
    trigger OnAfterInsertRecord()
    begin
        // Code to process imported data
    end;
}
```