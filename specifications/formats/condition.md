# Condition

A Condition has the following properties:

## Properties
| Name          | Type                                               | Remarks                                                                                                                                      |
|---------------|----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| FieldName     | [StringType](/specifications/formats/data-type.md) | Name of the field to filter (as known by the Connector)                                                                                      | 
 | CompareMethod | [StringType](/specifications/formats/data-type.md) | One of the values in [CompareMethod](/specifications/formats/compare-method.md)                                                              |  
 | DataType      | [StringType](/specifications/formats/data-type.md) | One of the values in [DataType](/specifications/formats/data-type.md)                                                                        | 
 | CompareData   | JSON                                               | Value(s) to compare with. Expressed in the value given by the DataType property. See [CompareData](/specifications/formats/compare-data.md). |


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
