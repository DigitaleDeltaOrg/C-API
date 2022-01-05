# Connector

The Connector is the component that response to a consumer's query, communicate with the plug-in to retrieve information and pass the collected data back to the consumer.

## Endpoints

The Connector must implement the following endpoints and respond accordingly:

### End-points table
| End-point           | Type                 | Request                                                | Response                                                                                      |
|---------------------|----------------------|--------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| /sources            | Functional discovery | -                                                      | Simple JSON array of [Source](/specifications/formats/source.md)s                             |
| /capabilities       | Functional discovery | -                                                      | Simple JSON array of [Connector capability](/specifications/formats/connector-capability.md)s |
| /compartments       | Data discovery       | -                                                      | Simple JSON array of [Compartment](/specifications/formats/compartment.md)s                   |
| /parameter          | Data discovery       | -                                                      | Simple JSON array of [Parameter](/specifications/formats/parameter.md)s                       |
| /measurementobjects | Data discovery       | -                                                      | Simple JSON array of [Compartment](/specifications/formats/compartment.md)s                   |
| /quantities         | Data discovery       | -                                                      | Simple JSON array of [Quantity](/specifications/formats/quantity.md)s                         |
| /units              | Data discovery       | -                                                      | Simple JSON array of [Unit](/specifications/formats/unit.md)s                                 |
| /measurements       | Measurements         | [Measurements](/specifications/formats/measurement.md) | Simple JSON array of [Measurement](/specifications/formats/measurement.md)s                   |


## Responsibilities

The responsibilities of the connector are:

- USE HTTPS, not HTTP! Authentication must never be transmitted by HTTP.
- Provide correct information to the end-points (see [end-points table](#end-points-table)).
- Answer to incoming request from caller (sources + query)
- Obtain plug-in information (from storage)
- Translate query to exchange format
- Send configuration information and query to plug-in (if the platform allows it, in parallel)
- Wait for plug-ins to send responses
- Handle issues
- Gather statistics
- Combine plug-in responses
- Send combined plug-in responses to caller
- Provide means to determine what sources provide what information, i.e. what parameters, compartments, quantities.
- Return the correct responses to the [Consumer](/architecture/consumer.md).
