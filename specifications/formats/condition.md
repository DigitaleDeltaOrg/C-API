# Condition

A Condition is a combination of FieldName, [CompareMethod](/specifications/formats/compare-method.md), [DataType](/specifications/formats/data-type.md) and [CompareData](/specifications/formats/compare-data.md) in a JSON structure:

```json
{
  "FieldName": "quantity",
  "CompareMethod": "In",
  "DataType": "ArrayOfStringType",
  "CompareData": [
    "WATHTE",
    "Q"
  ]
}
```
