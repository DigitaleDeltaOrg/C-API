# Architecture

The architecture of the C-API is purely based on HTTPS and JSON.

## Flow

[![Flow](https://mermaid.ink/img/eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG4gICAgcGFydGljaXBhbnQgQ29uc3VtZXJcbiAgICBwYXJ0aWNpcGFudCBDb25uZWN0b3JcbiAgICBwYXJ0aWNpcGFudCBQbHVnaW5cbiAgICBwYXJ0aWNpcGFudCBEYXRhU291cmNlXG4gICAgXG4gICAgQ29uc3VtZXItPkNvbm5lY3RvcjogUGFzcyBxdWVyeSBhbmQgc291cmNlc1xuICAgIGxvb3AgRm9yIGVhY2ggc291cmNlIHNlbGVjdGVkIGJ5IENvbnN1bWVyIChpbiBwYXJhbGxlbClcbiAgICAgIENvbm5lY3Rvci0-UGx1Z2luOiBDYWxsIHBsdWdpbiB3aXRoIHF1ZXJ5IGFuZCBTb3VyY2VEZWZpbml0aW9uXG4gICAgICBhY3RpdmF0ZSBQbHVnaW5cbiAgICAgIGxvb3AgRm9yIGFsbCBwYWdlcyB3aXRoIGRhdGEgdGhhdCBzYXRpZnkgdGhlIHF1ZXJ5XG4gICAgICAgIFBsdWdpbi0tPiBEYXRhU291cmNlOiBHZXQgZGF0YSBwYWdlXG4gICAgICAgIGFjdGl2YXRlIERhdGFTb3VyY2VcbiAgICAgICAgRGF0YVNvdXJjZS0tPiAtUGx1Z2luOiAnUmF3JyBEYXRhXG4gICAgICBlbmRcbiAgICBlbmRcbiAgICBQbHVnaW4tLT4gLUNvbm5lY3RvcjogVHJhbnNsYXRlZCBkYXRhXG4gICAgQ29ubmVjdG9yLS0-IENvbnN1bWVyOiBDb21waWxlZCBkYXRhXG4gICAgIiwibWVybWFpZCI6eyJ0aGVtZSI6ImRhcmsifSwidXBkYXRlRWRpdG9yIjpmYWxzZSwiYXV0b1N5bmMiOnRydWUsInVwZGF0ZURpYWdyYW0iOmZhbHNlfQ)](https://mermaid.live/edit#eyJjb2RlIjoic2VxdWVuY2VEaWFncmFtXG4gICAgcGFydGljaXBhbnQgQ29uc3VtZXJcbiAgICBwYXJ0aWNpcGFudCBDb25uZWN0b3JcbiAgICBwYXJ0aWNpcGFudCBQbHVnaW5cbiAgICBwYXJ0aWNpcGFudCBEYXRhU291cmNlXG4gICAgXG4gICAgQ29uc3VtZXItPkNvbm5lY3RvcjogUGFzcyBxdWVyeSBhbmQgc291cmNlc1xuICAgIGxvb3AgRm9yIGVhY2ggc291cmNlIHNlbGVjdGVkIGJ5IENvbnN1bWVyIChpbiBwYXJhbGxlbClcbiAgICAgIENvbm5lY3Rvci0-UGx1Z2luOiBDYWxsIHBsdWdpbiB3aXRoIHF1ZXJ5IGFuZCBTb3VyY2VEZWZpbml0aW9uXG4gICAgICBhY3RpdmF0ZSBQbHVnaW5cbiAgICAgIGxvb3AgRm9yIGFsbCBwYWdlcyB3aXRoIGRhdGEgdGhhdCBzYXRpZnkgdGhlIHF1ZXJ5XG4gICAgICAgIFBsdWdpbi0tPiBEYXRhU291cmNlOiBHZXQgZGF0YSBwYWdlXG4gICAgICAgIGFjdGl2YXRlIERhdGFTb3VyY2VcbiAgICAgICAgRGF0YVNvdXJjZS0tPiAtUGx1Z2luOiAnUmF3JyBEYXRhXG4gICAgICBlbmRcbiAgICBlbmRcbiAgICBQbHVnaW4tLT4gLUNvbm5lY3RvcjogVHJhbnNsYXRlZCBkYXRhXG4gICAgQ29ubmVjdG9yLS0-IENvbnN1bWVyOiBDb21waWxlZCBkYXRhXG4gICAgIiwibWVybWFpZCI6IntcbiAgXCJ0aGVtZVwiOiBcImRhcmtcIlxufSIsInVwZGF0ZUVkaXRvciI6ZmFsc2UsImF1dG9TeW5jIjp0cnVlLCJ1cGRhdGVEaWFncmFtIjpmYWxzZX0)

The [Consumer](/architecture/consumer.md) sends their query and the names of the data sources of interest to the [Connector](/architecture/connector.md).

The [Connector](/architecture/connector.md) determines what [Plug-in](/architecture/plug-in.md) is responsible for accessing that data and sends the corresponding configuration information ([Source definition](/specifications/formats/source-definition.md)) to the [Plug-in](/architecture/plug-in.md).

The [Plug-in](/architecture/plug-in.md) requests access to the data source, constructs the queries in the syntax that the data source understands and retrieves the data from the source.

If the consumer's query has aspects the data source does not understand, the [Plug-in](/architecture/plug-in.md) will perform extra filtering so that the data conforms to the request.

The [Plug-in](/architecture/plug-in.md) translates and converts the data to make it conform to the C-API standard.

Finally, it returns the data to the [Connector](/architecture/connector.md).

The [Connector](/architecture/connector.md) waits for the responses of the [Plug-in](/architecture/plug-in.md)s, combines the data and returns it to the consumer.

## Specification and implementation

The C-API is a specification. It defined how components are to behave and what messages they send to each other.

To simplify implementation and not to define what language or platform is required **and** allow as much flexibility as possible, only HTTP and JSON are used in the specification.

However, sample implementations are provided for the [Connector](/architecture/connector.md) and
[Plug-in](/architecture/plug-in.md)s for the  [DD-API](https://github.com/DigitaleDeltaOrg/dd-api), the [DD-ECO-API](https://github.com/DigitaleDeltaOrg/dd-eco-api) and [Z-INFO](https://www.hetwaterschapshuis.nl/z-info), as a proof of concept, in a [separate source repository](https://github.com/DigitaleDeltaOrg/C-API-poc-dotnet).
The examples are in [C# 10](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-10) / [.NET 6](https://dotnet.microsoft.com/en-us/download/dotnet/6.0). The code is therefor already largely OS independent.
Porting the code to other platforms and languages should not be a difficult task.

All [Plug-in](/architecture/plug-in.md)s (and the core) have [OAS 3.x](https://www.openapis.org) definitions.
These are located [here](/open-api-definitions/index.md).

The [Connector](/architecture/connector.md) and the [Plug-in](/architecture/plug-in.md)s communicate exclusively by means of HTTP(S) and JSON. The messages are standardised.

The C-API does ***not*** define the following:

- If and how configuration is managed or stored
- If and how temporary results from [plug-in](/architecture/plug-in.md)s are stored
- How the components are to be implemented
- Managing [SourceDefinition](/specifications/formats/source-definition.md)
- Provide a UI for the Connector

These topics are not platform-agnostic. as it depends on the storage facility of the organisation designing the connector (database, flat-storage. memory), how configuration should be handled (organisation-specific requirements) or how (if desired) a user interface is presented (technology, specific group-requirements).

For demo purposes, a simple, yet useful [Connector](/architecture/connector.md) with plug-ins for [DD-API](https://github.com/DigitaleDeltaOrg/dd-api), [DD-ECO-API](https://github.com/DigitaleDeltaOrg/dd-eco-api) and [Z-INFO](https://www.hetwaterschapshuis.nl/z-info) are available at [https://c-api-connector.ecosys.nl](https://c-api-connector-demo.ecosys.nl).
If you wish to have your own [plug-in](/architecture/plug-in.md) show-cased on the demo site, please contact [geri.wolters@ecosys.nl](mailto://geri.wolters@ecosys.nl).

[Connector](/architecture/connector.md)s and [plug-in](/architecture/plug-in.md)s do **not** need to be open source. It is, however, encouraged to use as much open source as possible.


# Challenges and solutions

During the project, with DD-API, DD-ECO-API and Z-INFO, several issues came up:

- [Time-series and observation-based measurements don't mix well](/specifications/timeseries-or-observations.md).
- [Handling paging](/specifications/handling-paging.md).
- [Common query format, Filter syntax](/specifications/filter-syntax.md).
- [Implementation differences](/specifications/implementation-differences.md).
- [Data standards](/specifications/data-standards.md).
- [Z-INFO does not expose any coordinates](/architecture/unsolved/z-info-does-not-export-any-coordinates.md).

## Topics left undefined

The C-API does ***not*** define the following:

- If or how temporary results from plug-ins are to be stored
- How the components are to be implemented, what language, framework, platform or operating system
- How to manage, configure or store [SourceDefinition](/specifications/formats/source-definition.md)
- If or how to implement the UI for the [Connector](/architecture/connector.md)
- What and how a [Consumer](/architecture/consumer.md) can access the [Connector](/architecture/connector.md)

These topics are left to the implementors of the [Connector](/architecture/connector.md) and [plug-in](/architecture/plug-in.md)s, or organisations implementing the C-API definitions. These topics are considered outside the scope of the C-API specification.

Other topics that are not platform-dependent, but still need to be defined at some stage:

- Certification
- Versioning
- Data catalogues

## Unsolved

- [Coordinates](/architecture/unsolved/coordinates.md)
- [Z-INFO and Coordinates](/architecture/unsolved/z-info-does-not-export-any-coordinates.md)
