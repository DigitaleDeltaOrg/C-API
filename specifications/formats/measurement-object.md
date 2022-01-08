# Measurement object (location)

Defines the subject under test.

## Properties
| Name     | Type                                               | Remarks                                                                       |
|----------|----------------------------------------------------|-------------------------------------------------------------------------------|
| code     | [StringType](/specifications/formats/data-type.md) | Code of the measurement object                                                |
| name     | [StringType](/specifications/formats/data-type.md) | Name (or description) of the measurement object                               |
| geometry | [GeoJSON](https://geojson.org)                     | Name (or description) of the measurement object (recommended)                 |
| source   | [StringType](/specifications/formats/data-type.md) | Code of the source as provided by the [Connector](/architecture/connector.md) |
