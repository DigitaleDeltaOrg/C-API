# Plug-In

Plug-Ins can either be generic or specific.

Generic plug-ins are capable of connecting to multiple data sources, provided they 'speak the same dialect'.
Dialect, in this case, means they connect to a data source using the same specifications, i.e. DD-API or DD-ECO-API.
Since, even if they speak the same dialect, the implementations may not be the same (i.e. naming of parameters may differ or specific filtering is not available).
The Connector can provide the plug-in with a dictionary that can translate names or even [data categories](/specifications/formats/data-category.md) and insight in the capabilities of the source. The plug-in can then take appropriate actions.

## End-points

The Plug-in must implement the following endpoints and respond accordingly:

### End-points table
| End-point           | Type                 | In                                               | Out                                                                         |
|---------------------|----------------------|--------------------------------------------------|-----------------------------------------------------------------------------|
| /sources            | Functional discovery | -                                                | Simple JSON array of [Source](/specifications/formats/source.md)s           |
| /compartments       | Data discovery       | -                                                | Simple JSON array of [Compartment](/specifications/formats/compartment.md)s |
| /parameter          | Data discovery       | -                                                | Simple JSON array of [Parameter](/specifications/formats/parameter.md)s     |
| /measurementobjects | Data discovery       | -                                                | Simple JSON array of [Compartment](/specifications/formats/compartment.md)s |
| /quantities         | Data discovery       | -                                                | Simple JSON array of [Quantity](/specifications/formats/quantity.md)s       |
| /units              | Data discovery       | -                                                | Simple JSON array of [Unit](/specifications/formats/unit.md)s               |
| /measurements       | Measurements         | [DataBody](/specifications/formats/data-body.md) | [ResponseCache](/specifications/formats/measurement-response.md)            |

## Responsibilities

The responsibilities of the plug-in are:

- USE HTTPS, not HTTP! Authentication must never be transmitted by HTTP.
- Provide correct information to the end-points (see [end-points table](#end-points-table)).
- Interpret the Filter Syntax request from the [Connector](/architecture/connector.md).
- Convert the Filter Syntax to the filter-system that the data source understands.
- Handle authentication.
- Retrieve filtered data from the data source.
- Handle paging, if required by the data source.
- Provide additional filtering, if needed, that the data source doesn't understand.
- Handle error situations, if possible, otherwise inform the [Connector](/architecture/connector.md) by means of the [ResponseCache](/specifications/formats/measurement-response.md).
- Handle conversions, if needed, based on the information that the [Connector](/architecture/connector.md) provides.
- Convert the retrieved data to the C-API specification.
- Provide means to determine what the data source provides what information, i.e. what parameters, compartments, quantities.
- Return the correct responses to the [Connector](/architecture/connector.md).

The following functionality should be provided:

- Handle statistics ([ResponseCache](/specifications/formats/measurement-response.md)).
