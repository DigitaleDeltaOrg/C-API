# MeasurementResponse

MeasurementResponse is sent back to the [Connector](/architecture/connector.md) by the [Plug-in](/architecture/plug-in.md). The ResponseId field must match the ResponseId sent to the [Plug-in](/architecture/plug-in.md) by the [Connector](/architecture/connector.md).

```json
{
  "Id": "",
  "RequestId": "",
  "Measurements": {},
  "Statistics": {},
  "Errors": {},
  "HttpStatus": 200
}
```

Id is the Id of the Source as sent by the Connector in the SourceDefinition. Based on the combination Id and RequestId, this allows the Connector to temporary store the responses of the plug-ins and combine them.

Measurements is a list of observations ([Measurement](/specifications/formats/measurement.md)) entities.

TODO: Statistics is optional: it can be used to measure performance and usage.

TODO: Errors contain a list of HTTP statuses and their frequency that the plug-in encountered during processing the request. This information can be used to optimize the SourceDefinition.

HttpStatus is the status of the request by the plug-in. If the plug-in was able to handle errors from the data source (if they arose), it should return OK (Status 200). If not, it should return an error indicating the type of error it could not recover from.
