# MeasurementResponse

MeasurementResponse is sent back to the [Connector](/architecture/connector.md) by the [Plug-in](/architecture/plug-in.md). 

## Properties
| Name        | Type                                                           | Remarks                                                                                            |
|-------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| Source      | [StringType](/specifications/formats/data-type.md)             | Code of the source as passed by the [Connector](/architecture/connector.md)                        |
| RequestId   | [StringType](/specifications/formats/data-type.md)             | Id of the request, as passed by the [Connector](/architecture/connector.md)                        |
| Measurement | Array of [Measurement](/specifications/formats/measurement.md) | Array of measurements, retrieved and processed by the [Plug-in](/architecture/plug-in.md)          |
| Statistics  | [Statistics](/specifications/formats/statistics.md)            | Statistics information from the plug-in. Recommended.                                              |
| Errors      | [Error](/specifications/formats/error-type.md)                 | Represents the problems that the Plug-in](/architecture/plug-in.md) encountered during the request |
| HttpStatus  | [NumericType](/specifications/formats/data-type.md)            | HttpStatus representing the status of the [Plug-in](/architecture/plug-in.md) after processing.    |


```json
{
  "Source": "",
  "RequestId": "",
  "Measurements": {},
  "Statistics": {},
  "Errors": {},
  "HttpStatus": 200
}
```


Measurements is a list of observations ([Measurement](/specifications/formats/measurement.md)) entities.


HttpStatus is the status of the request by the plug-in. If the plug-in was able to handle errors from the data source (if they arose), it should return OK (Status 200). If not, it should return an error indicating the type of error it could not recover from.
