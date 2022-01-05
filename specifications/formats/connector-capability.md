# ConnectorCapability

The Connector defines what it offers the consumer as query capabilities. Capabilities are provided both to the plug-in and the consumer.

A capability consists of a field name, a [DataCategory](/specifications/formats/data-category.md)  and [QueryType](/specifications/formats/query-type.md).

```json
{
  "ConnectorCapabilities": [
    {
      "FieldName": "compartment",
      "DataCategory": "Compartment",
      "QueryType": "StringExact"
    },
    {
      "FieldName": "parameter",
      "DataCategory": "Parameter",
      "QueryType": "StringExact"
    },
    {
      "FieldName": "unit",
      "DataCategory": "Unit",
      "QueryType": "StringExact"
    },
    {
      "FieldName": "compartment",
      "DataCategory": "Compartment",
      "QueryType": "StringExact"
    },
    {
      "FieldName": "measurementobject",
      "DataCategory": "MeasurementObject",
      "QueryType": "StringWildCard"
    },
    {
      "FieldName": "quantity",
      "DataCategory": "Quantity",
      "QueryType": "StringExact"
    },
    {
      "FieldName": "measurementdate",
      "DataCategory": "Date",
      "QueryType": "Date"
    },
    {
      "FieldName": "value",
      "DataCategory": "Numeric",
      "QueryType": "Numeric"
    }
  ]
}
```
