# Text-based Filter Syntax (Connector)

A Filter Syntax query consists of one or more conditions. Each condition consists of three parts:

- Field name
- Compare method
- Compare data

These parts are separated by a colon. Conditions are separated by a semicolon.

Examples:

```html
?request=fieldname1:eq:'test';fieldname2:in:['test1', 'test2'];fieldname3:gt:123
```

The standard compare methods can be found [here](/specifications/formats/compare-method.md).

Plug-ins ***must*** support these compare methods and ***must*** translate these to the compare methods that the data source understands, and ***must*** implement these if the data source does not.

The C-API knows the following data formats:

- StringType: text, **always** quoted
- NumericType: **never** quoted, period is the decimal separator, no thousands separators, no scientific notations.
- DateType: ISO-8601 date/time format
- ArrayOfStringType: JSON notation of an array of **quoted** strings. JSON arrays start with \[ and end with \].
- ArrayOfNumericType: JSON notation of an array of numeric values. JSON arrays start with \[ and end with \].

## Structured Filter (Plug-In)


A structured filter basically is an expanded JSON version of the textual Filter Syntax, represented as an array of Condition.
The equivalent of the query above is:

```json
[
    {"FieldName": "fieldname1", "CompareMethod": "eq", "CompareData": "test"}, 
    {"FieldName": "fieldname2", "CompareMethod": "in", "CompareData": ["test1", "test2"]},
    {"FieldName": "fieldname3", "CompareMethod": "gt", "CompareData": 128}
]
```

Separating the query syntax that the user uses from the internal structured format allows for different schemes to be implemented.
