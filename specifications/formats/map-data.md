# MapData

Mapping data is passed as an array of MapData elements from the [Connector](/architecture/connector.md) to the [Plug-in](/architecture/plug-in.md):

A map data element consists of four fields:

## Properties
| Name               | Type                                               | Remarks                                                                                                                       |
|--------------------|----------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| cApiDataCategory   | [StringType](/specifications/formats/data-type.md) | Name of the [data category](/specifications/formats/data-category.md) as known by the [Connector](/architecture/connector.md) | 
| cApiName           | [StringType](/specifications/formats/data-type.md) | Value as  known by the [Connector](/architecture/connector.md)                                                                |  
| sourceDataCategory | [StringType](/specifications/formats/data-type.md) | Name of the [data category](/specifications/formats/data-category.md) as known by the [Plug-in](/architecture/plug-in.md)     | 
| sourceName         | [StringType](/specifications/formats/data-type.md) | Value as known by the [Plug-in](/architecture/plug-in.md)                                                                     |


The combination CApiDataCategory+CApiName must be mapped to SourceDataCategory+SourceName and vice versa.
Unknown combinations are left untouched (unmapped).

```json
{
  "MapData": [
    {
      "cApiDataCategory": "Quantity",
      "cApiName": "Q",
      "sourceDataCategory": "Parameter",
      "sourceName": "Q"
    },
    {
      "cApiDataCategory": "Quantity",
      "cApiName": "GELDHD",
      "sourceDataCategory": "Parameter",
      "sourceName": "EGV"
    },
    {
      "cApiDataCategory": "Quantity",
      "cApiName": "WATHTE",
      "sourceDataCategory": "Parameter",
      "sourceName": "WATHTE"
    },
    {
      "cApiDataCategory": "Quantity",
      "cApiName": "NEERSG",
      "sourceDataCategory": "Parameter",
      "sourceName": "NEERSG"
    },
    {
      "cApiDataCategory": "Quantity",
      "cApiName": "KRUINHTE",
      "sourceDataCategory": "Parameter",
      "sourceName": "KRUINHTE"
    }
  ]
}
```
