# DataType

The number of data types in C-API are limited. Their presentation is in JSON format.

Supported data types are:

## Data types
| Data type         | Presentation              | Remarks                                                                              |
|-------------------|---------------------------|--------------------------------------------------------------------------------------|
| StringType        | 'string'                  | Single or double quotes allowed, but must match.                                     |
| NumericType       | 123.456                   | Period as decimal separators. No thousands-separators or scientific notation allowed |
| DateType          | 'yyyy-MM-dd HH:mm:ss ttt' | Date in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format                    |
| ArrayOfStringType | \['string', 'string2'\]   | JSON array notation                                                                  |
| String            | \[123, 235\]              | JSON array notation                                                                  |

