# Data Exchange

The [DataBody](data-body.md) structure is sent by the [Connector](/architecture/connector.md) to the [Plug-in](/architecture/plug-in.md).
It contains [configuration data](source-definition.md) and the query, consisting of a list of [conditions](condition.md).
The [Plug-in](/architecture/plug-in.md) sends a [MeasurementResponse](measurement-response.md) as a response back to the [Connector](/architecture/connector.md).

The [Plug-in](/architecture/plug-in.md) in addition has to send (simple) lists of items back to the [Connector](/architecture/connector.md) when asked. This allows retrieval of quantities, parameters, units, compartments and measurement objects know by the data source.

The [Connector](/architecture/connector.md) can send this information back to the consumer, which in turn, can base queries on that information.
