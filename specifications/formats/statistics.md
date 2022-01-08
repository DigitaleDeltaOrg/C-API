# Statistics

For the [Connector](/architecture/connector.md) it can be important to have statistics on usage and performance of the [plug-in](/architecture/plug-in.md)s.

Therefor the [MeasurementResponse](/specifications/formats/measurement-response.md) can hold a Statics structure.
The statistics are in context of the current request that it received from the Connector.
It is defined as:

## Properties
| Name                       | Type                                                           | Remarks                                                                                   |
|----------------------------|----------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| source                     | [StringType](/specifications/formats/data-type.md)             | Code of the source as passed by the [connector](/architecture/connector.md)               |
| responseTimeInMilliseconds | [NumericType](/specifications/formats/data-type.md#data-types) | total time in milliseconds that the plug-in had to wait for response from the data source |
| totalByteCount             | [NumericType](/specifications/formats/data-type.md#data-types) | total number of bytes that the plug-in received from the data source                      |
| numberOfRequests           | [NumericType](/specifications/formats/data-type.md#data-types) | number of request the plug-in send to the data source                                     |

The implementation of this structure is recommended.

