# MapData

Mapping data is passed as an array of MapData elements from the Connector to the Plug-in:

A map data element consists of four fields:

CApiDataCategory is a [DataCategory](/specifications/formats/data-category.md) according to the C-API.

CApiName is the name of the item according to the C-API.

SourceDataCategory is a [DataCategory](/specifications/formats/data-category.md) according to the data source.

SourceName is the name of the item according to the data source.

Using this, the combination of CApiDataCategory+CApiName can be mapped to SourceDataCategory+SourceName and vice versa.

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
