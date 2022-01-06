# Measurement
A measurement consists of data from a (converted) observation.

## Properties
| Name              | Type                                                | Remarks     |
|-------------------|-----------------------------------------------------|-------------|
| Quantity          | [StringType](/specifications/formats/data-type.md)  |             |
| MeasurementObject | [StringType](/specifications/formats/data-type.md)  |             |
| MeasurementDate   | [DateType](/specifications/formats/data-type.md)    |             |
| Value             | [NumericType](/specifications/formats/data-type.md) |             |
| Coordinates       | [GeoJSON](https://geojson.org)                      | Recommended |
| Compartment       | [StringType](/specifications/formats/data-type.md)  | Recommended |
| Unit              | [StringType](/specifications/formats/data-type.md)  | Recommended |
| AdditionalData    | Dictionary of key-value pairs                       | Recommended |


In [AQUO](https://www.aquo.nl), when a unit is not specified, the value DIMSLS (dimensionless) is required.

```json
{
  "Quantity": "",
  "Parameter": "",
  "MeasurementObject": "",
  "MeasurementDate": "",
  "Coordinates": {},
  "Compartment": "",
  "Unit": "",
  "Value": "",
  "AdditionalData": {}
}
```
