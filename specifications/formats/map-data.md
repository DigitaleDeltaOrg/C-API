# MapData

Mapping data is passed as an array of MapData elements from the [Connector](/architecture/connector.md) to the [Plug-in](/architecture/plug-in.md):

A map data element consists of four fields:

## Properties
| Name               | Type                                               | Remarks                                                                                                                       |
|--------------------|----------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| CApiDataCategory   | [StringType](/specifications/formats/data-type.md) | Name of the [data category](/specifications/formats/data-category.md) as known by the [Connector](/architecture/connector.md) | 
| CApiName           | [StringType](/specifications/formats/data-type.md) | Value as  known by the [Connector](/architecture/connector.md)                                                                |  
| SourceDataCategory | [StringType](/specifications/formats/data-type.md) | Name of the [data category](/specifications/formats/data-category.md) as known by the [Plug-in](/architecture/plug-in.md)     | 
| SourceName         | [StringType](/specifications/formats/data-type.md) | Value as known by the [Plug-in](/architecture/plug-in.md)                                                                     |


The combination CApiDataCategory+CApiName must be mapped to SourceDataCategory+SourceName and vice versa.
Unknown combinations are left untouched (unmapped).

```json
{
  "MapData": [
    {
      "CApiDataCategory": "Quantity",
      "CApiName": "Q",
      "SourceDataCategory": "Parameter",
      "SourceName": "Q"
    },
    {
      "CApiDataCategory": "Quantity",
      "CApiName": "GELDHD",
      "SourceDataCategory": "Parameter",
      "SourceName": "EGV"
    },
    {
      "CApiDataCategory": "Quantity",
      "CApiName": "WATHTE",
      "SourceDataCategory": "Parameter",
      "SourceName": "WATHTE"
    },
    {
      "CApiDataCategory": "Quantity",
      "CApiName": "NEERSG",
      "SourceDataCategory": "Parameter",
      "SourceName": "NEERSG"
    },
    {
      "CApiDataCategory": "Quantity",
      "CApiName": "KRUINHTE",
      "SourceDataCategory": "Parameter",
      "SourceName": "KRUINHTE"
    }
  ]
}
```
