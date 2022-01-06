# Specifications

This section deals with the specifications that make up the C-API.
This includes information such as a description of the request- and response formats.

- [Formats](/specifications/formats/formats.md)

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

