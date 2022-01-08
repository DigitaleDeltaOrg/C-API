# ConnectorCapability

The Connector defines what it offers the consumer as query capabilities. Capabilities are provided both to the plug-in and the consumer.

A capability consists of a field name, a [DataCategory](/specifications/formats/data-category.md)  and [QueryType](/specifications/formats/query-type.md).

## Properties
| Name         | Type                                               | Remarks                                                                          |
|--------------|----------------------------------------------------|----------------------------------------------------------------------------------|
| fieldName    | [StringType](/specifications/formats/data-type.md) | Name of the field                                                                |
| dataCategory | [StringType](/specifications/formats/data-type.md) | One of the values in [data categories](/specifications/formats/data-category.md) |
| queryType    | [StringType](/specifications/formats/data-type.md) | One of the values in [query types](/specifications/formats/query-type.md)        |


```json
{
  "ConnectorCapabilities": [
    {
      "fieldName": "compartment",
      "dataCategory": "Compartment",
      "queryType": "StringExact"
    },
    {
      "fieldName": "parameter",
      "dataCategory": "Parameter",
      "queryType": "StringExact"
    },
    {
      "fieldName": "unit",
      "dataCategory": "Unit",
      "queryType": "StringExact"
    },
    {
      "fieldName": "compartment",
      "dataCategory": "Compartment",
      "queryType": "StringExact"
    },
    {
      "fieldName": "measurementobject",
      "dataCategory": "MeasurementObject",
      "queryType": "StringWildCard"
    },
    {
      "fieldName": "quantity",
      "dataCategory": "Quantity",
      "queryType": "StringExact"
    },
    {
      "fieldName": "measurementdate",
      "dataCategory": "Date",
      "queryType": "Date"
    },
    {
      "fieldName": "value",
      "dataCategory": "Numeric",
      "queryType": "Numeric"
    }
  ]
}
```
