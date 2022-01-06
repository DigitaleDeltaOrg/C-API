# Definitions
First some definitions used in this specification:


| Definition                                                        | Description                                                                                                      |
|-------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| [Consumer](/architecture/consumer.md)                             | the person or system requesting data                                                                             |
| [Provider](/architecture/provider.md)                             | system offering one or more components of this specification                                                     |
| [Data source](/architecture/data-source.md)                       | container for measurement data                                                                                   |
| [Connector](/architecture/connector.md)                           | an active component that interacts with Consumer                                                                 |
| [Plug-in](/architecture/plug-in.md)                               | an active components that gathers data from a data source and translates that data back to a standardised format |
| [Source definition](/specifications/formats/source-definition.md) | configuration data                                                                                               |

As this is a specification and the language used in specifications matter, here are some keywords and how they have to be handled:


| this...     | means...                        |
|-------------|---------------------------------|
| must, shall | it is required                  |
| should      | it is recommended, but optional |
| could       | it is suggested, so optional    |