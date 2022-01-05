# C-API (Convenience API)

## Introduction

In the world of measurements many standards and software-specific interfaces exist, suited for specific circumstances.

To name a few in the water-world:

* [DD-API](https://github.com/DigitaleDeltaOrg/dd-api) for time series-based measurements
* [DD-ECO-API](https://github.com/DigitaleDeltaOrg/dd-eco-api) for observation-based measurements
* [Z-INFO](https://www.hetwaterschapshuis.nl/z-info) for waste-water management, also observation-based

These systems are connected in some form, and this means that the data from these systems, are connected as well.

One of the challenges is how to combine data from these disparate systems.

The C-API attempts to provide a means to that end.

## C-API

In our connected world, the data from these diverse systems needs to be combined to be able to produce meaningful data.

But combining the data from these systems is not a trivial task. The systems have different query interfaces, different naming conventions, different export formats, etc. Some provide data in smaller sections (paging).
Manually combining the data is error-prone, and since decisions may be made based on that data, potentially harmful.

The C-API attempts to make gathering the data more... convenient. It does that by providing a single, but flexible query format and export format.

It has a plug-in architecture that allows additional data-sources to be added. The plug-ins take care of querying the data source using a standardised query format and returning the data in the standardised export format.

The C-API in this form is classified as a pilot project as there are some [unknowns](#topics-left-undefined). De code produced to visualize this project has the status of Proof of Concept.

First some definitions used in this specification:


| Definition                                                        | Description                                                                                                      |
| ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| [Consumer](/architecture/consumer.md)                             | the person or system requesting data                                                                             |
| [Provider](/architecture/provider.md)                             | system offering one or more components of this specification                                                     |
| [Data source](/architecture/data-source.md)                       | container for measurement data                                                                                   |
| [Connector](/architecture/connector.md)                           | an active component that interacts with Consumer                                                                 |
| [Plug-in](/architecture/plug-in.md)                               | an active components that gathers data from a data source and translates that data back to a standardised format |
| [Source definition](/specifications/formats/source-definition.md) | configuration data                                                                                               |

As this is a specification and the language used in specifications matter, here are some keywords and how they have to be handled:


| this...     | means...                        |
| ------------- | --------------------------------- |
| must, shall | it is required                  |
| should      | it is recommended, but optional |
| could       | it suggested, so optional       |

On to the architecture...

## Architecture

The architecture of the C-API is purely based on HTTPS and JSON.

### Flow

[![Flow](https://mermaid.ink/img/eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG4gICAgcGFydGljaXBhbnQgQ29uc3VtZXJcbiAgICBwYXJ0aWNpcGFudCBDb25uZWN0b3JcbiAgICBwYXJ0aWNpcGFudCBQbHVnaW5cbiAgICBwYXJ0aWNpcGFudCBEYXRhU291cmNlXG4gICAgXG4gICAgQ29uc3VtZXItPkNvbm5lY3RvcjogUGFzcyBxdWVyeSBhbmQgc291cmNlc1xuICAgIGxvb3AgRm9yIGVhY2ggc291cmNlIHNlbGVjdGVkIGJ5IENvbnN1bWVyIChpbiBwYXJhbGxlbClcbiAgICAgIENvbm5lY3Rvci0-UGx1Z2luOiBDYWxsIHBsdWdpbiB3aXRoIHF1ZXJ5IGFuZCBTb3VyY2VEZWZpbml0aW9uXG4gICAgICBhY3RpdmF0ZSBQbHVnaW5cbiAgICAgIGxvb3AgRm9yIGFsbCBwYWdlcyB3aXRoIGRhdGEgdGhhdCBzYXRpZnkgdGhlIHF1ZXJ5XG4gICAgICAgIFBsdWdpbi0tPiBEYXRhU291cmNlOiBHZXQgZGF0YSBwYWdlXG4gICAgICAgIGFjdGl2YXRlIERhdGFTb3VyY2VcbiAgICAgICAgRGF0YVNvdXJjZS0tPiAtUGx1Z2luOiAnUmF3JyBEYXRhXG4gICAgICBlbmRcbiAgICBlbmRcbiAgICBQbHVnaW4tLT4gLUNvbm5lY3RvcjogVHJhbnNsYXRlZCBkYXRhXG4gICAgQ29ubmVjdG9yLS0-IENvbnN1bWVyOiBDb21waWxlZCBkYXRhXG4gICAgIiwibWVybWFpZCI6eyJ0aGVtZSI6ImRhcmsifSwidXBkYXRlRWRpdG9yIjpmYWxzZSwiYXV0b1N5bmMiOnRydWUsInVwZGF0ZURpYWdyYW0iOmZhbHNlfQ)](https://mermaid.live/edit#eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG4gICAgcGFydGljaXBhbnQgQ29uc3VtZXJcbiAgICBwYXJ0aWNpcGFudCBDb25uZWN0b3JcbiAgICBwYXJ0aWNpcGFudCBQbHVnaW5cbiAgICBwYXJ0aWNpcGFudCBEYXRhU291cmNlXG4gICAgXG4gICAgQ29uc3VtZXItPkNvbm5lY3RvcjogUGFzcyBxdWVyeSBhbmQgc291cmNlc1xuICAgIGxvb3AgRm9yIGVhY2ggc291cmNlIHNlbGVjdGVkIGJ5IENvbnN1bWVyIChpbiBwYXJhbGxlbClcbiAgICAgIENvbm5lY3Rvci0-UGx1Z2luOiBDYWxsIHBsdWdpbiB3aXRoIHF1ZXJ5IGFuZCBTb3VyY2VEZWZpbml0aW9uXG4gICAgICBhY3RpdmF0ZSBQbHVnaW5cbiAgICAgIGxvb3AgRm9yIGFsbCBwYWdlcyB3aXRoIGRhdGEgdGhhdCBzYXRpZnkgdGhlIHF1ZXJ5XG4gICAgICAgIFBsdWdpbi0tPiBEYXRhU291cmNlOiBHZXQgZGF0YSBwYWdlXG4gICAgICAgIGFjdGl2YXRlIERhdGFTb3VyY2VcbiAgICAgICAgRGF0YVNvdXJjZS0tPiAtUGx1Z2luOiAnUmF3JyBEYXRhXG4gICAgICBlbmRcbiAgICBlbmRcbiAgICBQbHVnaW4tLT4gLUNvbm5lY3RvcjogVHJhbnNsYXRlZCBkYXRhXG4gICAgQ29ubmVjdG9yLS0-IENvbnN1bWVyOiBDb21waWxlZCBkYXRhXG4gICAgIiwibWVybWFpZCI6IntcbiAgXCJ0aGVtZVwiOiBcImRhcmtcIlxufSIsInVwZGF0ZUVkaXRvciI6ZmFsc2UsImF1dG9TeW5jIjp0cnVlLCJ1cGRhdGVEaWFncmFtIjpmYWxzZX0)

The [Consumer](/architecture/consumer.md) sends their query and the names of the data sources of interest to the [Connector](/architecture/connector.md).

The [Connector](/architecture/connector.md) determines what [Plug-in](/architecture/plug-in.md) is responsible for accessing that data and sends the corresponding configuration information ([Source definition](/specifications/formats/source-definition.md)) to the [Plug-in](/architecture/plug-in.md).

The [Plug-in](/architecture/plug-in.md) requests access to the data source, constructs the queries in the syntax that the data source understands and retrieves the data from the source.

If the consumer's query has aspects the data source does not understand, the [Plug-in](/architecture/plug-in.md) will perform extra filtering so that the data conforms to the request.

The [Plug-in](/architecture/plug-in.md) translates and converts the data to make it conform to the C-API standard.

Finally, it returns the data to the [Connector](/architecture/connector.md).

The [Connector](architecture/connector.md) waits for the responses of the [Plug-in](/architecture/plug-in.md)s, combines the data and returns it to the consumer.

### Specification and implementation

The C-API is a specification. It defined how components are to behave and what messages they send to each other.

To simplify implementation and not to define what language or platform is required **and** allow as much flexibility as possible, only HTTP and JSON are used in the specification.

However, sample implementations are provided for the [Connector](/architecture/connector.md) and
[Plug-in](/architecture/plug-in.md)s for the DD-API, the DD-ECO-API and [Z-INFO](https://www.hetwaterschapshuis.nl/z-info), as a proof of concept, in a [separate source repository](https://github.com/DigitaleDeltaOrg/C-API-poc-dotnet). The examples are in C# 10/.NET 6. Porting the code to other platforms and languages should not be a difficult task.

All plug-ins (and the core) have OAS 3.x definitions. The Connector and the plug-ins communicate exclusively by means of HTTP(S) and JSON. The messages are standardised.

The C-API does ***not*** define the following:

- If and how configuration is managed or stored
- If and how temporary results from plug-ins is stored
- How the components are to be implemented
- Managing SourceDefinition
- Provide a UI for the Connector

These topics are not platform-agnostic. as it depends on the storage facility of the organisation designing the connector (database, flat-storage. memory), how configuration should be handled (organisation-specific requirements) or how (if desired) a user interface is presented (technology, specific group-requirements).

For demo purposes, a simple, yet useful [Connector](/architecture/connector.md) with plug-ins for [DD-API](https://github.com/DigitaleDeltaOrg/dd-api), [DD-ECO-API](https://github.com/DigitaleDeltaOrg/dd-eco-api) and [Z-INFO](https://www.hetwaterschapshuis.nl/z-info) are available at [https://c-api-connector.ecosys.nl](https://c-api-connector-demi.ecosys.nl).
If you wish to have your own [plug-in](/architecture/plug-in.md) show-cased on the demo site, please contact [geri.wolters@ecosys.nl](mailto://geri.wolters@ecosys.nl).

## History

The C-API is a brain child of Johannes Meerding of [Hoogheemraadschap van Delfland](https://www.hhdelfland.nl) (HvD), to attempt to combine measurements from different sources.

Faced by the fact that different systems had different interfaces, different query languages and different formats, and some systems did not even provide a method to export data for data analysis, he started this project.

The initial version was designed and developed by [EcoSys](https://www.ecosys.nl) on request of [HvD](https://www.hhdelfland.nl). [HvD](https://www.hhdelfland.nl) graciously donated the project to Open Source. [Informatiehuis Water](https://www.ihw.nl) is governing this specification as a member of the [Digital Delta family of standards](https://digitaledeltaorg.github.io).

## Challenges and solutions

During the project, with DD-API, DD-ECO-API and Z-INFO, several issues came up:

- [Time-series and observation-based measurements don't mix well](/specifications/timeseries-or-observations.md).
- [Handling paging](/specifications/handling-paging.md).
- [Common query format, Filter syntax](/specifications/filter-syntax.md).
- [Implementation differences](/specifications/implementation-differences.md).
- [Data standards](/specifications/data-standards.md).
- [Z-INFO does not expose any coordinates](/architecture/unsolved/z-info-does-not-export-any-coordinates.md).

## Topics left undefined

The C-API does ***not*** define the following:

If and how temporary results from plug-ins is stored

- How the components are to be implemented
- Managing, configuring and storing [SourceDefinition](/specifications/formats/source-definition.md)
- Provide a UI for the [Connector](/architecture/connector.md)
- What Consumer can access the [Connector](/architecture/connector.md) and how

These topics are left to the implementors of the [Connector](/architecture/connector.md) and [plug-in](/architecture/plug-in.md)s, or organisations implementing the C-API definitions. These topics are considered outside the scope of the C-API specification.

Other topics that are not platform-dependent, but still need to be defined at some stage:

- Certification
- Versioning
- Data catalogues

## Unsolved

- [Coordinates](/architecture/unsolved/coordinates.md)
- [Z-INFO and Coordinates](/architecture/unsolved/z-info-does-not-export-any-coordinates.md)

### Thank you!

Big thanks go to the following organisations:

[Hoogheemraadschap van Delfland](https://www.hhdelfland.nl) for providing the data from their WIS system for the pilot to expose DD-API data and their data for Z-INFO and bringing this project to life.

[Aquon](https://www.aquon.nl) for allowing access to the ecological data of Delfland via the DD-ECO-API.

[Hoogheemraadschap Hollands Noorderkwartier](https://www.hhnk.nl) for providing ecological and chemical data of their organisation through DD-ECO-API.

[Informatiehuis Water](https://www.ihw.nl) for willing to govern this project.

## Project members

Current project members can be found [here](/project-members.md)

## Plug-ins

See the [plug-in catalogue](/catalogue/available-plug-ins.md) for available plug-ins.
