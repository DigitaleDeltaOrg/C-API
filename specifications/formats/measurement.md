# Measurement
A measurement consists of data from a (converted) observation.

Required:
- Quantity
- MeasurementObject
- MeasurementDate
- Value

Coordinates are expressed in GeoJSON. The default coordinate system for GeoJSON is WGS84.
The GeoJSON standard specifically states that there is no standard method to convey other coordinate systems.
The parties involved have to decide themselves how to handle it.
One method to add a property that specifies the coordinate system to use.

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
