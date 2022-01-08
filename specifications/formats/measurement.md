# Measurement
A measurement consists of data from a (converted) observation.

## Properties
| Name              | Type                                                | Remarks     |
|-------------------|-----------------------------------------------------|-------------|
| quantity          | [StringType](/specifications/formats/data-type.md)  |             |
| measurementObject | [StringType](/specifications/formats/data-type.md)  |             |
| measurementDate   | [DateType](/specifications/formats/data-type.md)    |             |
| value             | [NumericType](/specifications/formats/data-type.md) |             |
| coordinates       | [GeoJSON](https://geojson.org)                      | Recommended |
| compartment       | [StringType](/specifications/formats/data-type.md)  | Recommended |
| unit              | [StringType](/specifications/formats/data-type.md)  | Recommended |
| additionalData    | Dictionary of key-value pairs                       | Recommended |


In [AQUO](https://www.aquo.nl), when a unit is not specified, the value DIMSLS (dimensionless) is required.

```json
{
  "quantity": "",
  "parameter": "",
  "measurementObject": "",
  "measurementDate": "",
  "coordinates": {},
  "compartment": "",
  "unit": "",
  "value": "",
  "additionalData": {}
}
```
