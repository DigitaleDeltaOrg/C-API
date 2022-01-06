# Measurement object (location)

Defines the subject under test.

## Properties
| Name     | Type                                               | Remarks                                                                       |
|----------|----------------------------------------------------|-------------------------------------------------------------------------------|
| Code     | [StringType](/specifications/formats/data-type.md) | Code of the measurement object                                                |
| Name     | [StringType](/specifications/formats/data-type.md) | Name (or description) of the measurement object                               |
| Geometry | [GeoJSON](https://geojson.org)                     | Name (or description) of the measurement object (recommended)                 |
| Source   | [StringType](/specifications/formats/data-type.md) | Code of the source as provided by the [Connector](/architecture/connector.md) |
