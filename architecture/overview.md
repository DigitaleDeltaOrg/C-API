# Architecture Overview

## Definitions

To avoid differences in interpretations, this specification uses some definitions.

- Consumer: the person or system that requests data
- Data source: container for measurement data
- [Connector](/architecture/connector.md): an active component that interacts with Consumer
- [Plug-in](/architecture/plug-in.md): an active components that gathers data from a data source and translates that data back to a standardised format

Also see [data categories](/specifications/formats/data-categories.md).

## Architecture

The architecture of the C-API is simple: it consists of three components:
- The [Connector](/architecture/connector.md) is the interface between the consumer and the plug-ins.
- The [Plug-In](/architecture/plug-in.md)s communicate with the data sources
- The [SourceDefinition](/specifications/formats/source-definition.md) is a configuration item that is governed by the Connector and passed to the Plug-In. It contains information such as authentication data and conversions.

The [Connector](connector.md) and the [Plug-In](/architecture/plug-in.md)s communicate by [JSON](https://nl.wikipedia.org/wiki/JSON) messages via [HTTP(S)](https://nl.wikipedia.org/wiki/HyperText_Transfer_Protocol_Secure) POSTs. The [Connector](/architecture/connector.md) is also called via HTTP(S), but by means of a GET.

The [Plug-In](/architecture/plug-in.md)s are not meant to be called directly from a browser. CORS issues with POSTs should therefore not matter.
They can be tested, however, using tools such as [wget](https://en.wikipedia.org/wiki/Wget), [cURL](https://en.wikipedia.org/wiki/CURL) or [PostMan](https://www.postman.com).

Since nothing more than [JSON](https://nl.wikipedia.org/wiki/JSON) and [HTTP(S)](https://nl.wikipedia.org/wiki/HyperText_Transfer_Protocol_Secure) is required, the architecture is platform and language-agnostic. Any language/framework that can process these requirements can be used.

