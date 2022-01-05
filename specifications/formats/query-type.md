# QueryType
A query type is a convenient placeholder for one or more compare methods.
Based on the query type, the plug-in can determine what types of comparisons it should pass to the data source, or handle it itself.

The following types are available:

## QueryType to CompareMethods
| QueryType      | CompareMethods                     |
|----------------|------------------------------------|
| StringExact    | eq, ne, in, notin                  |
| StringWildCard | eq, ne, startswith, like, endswith |
| Date           | eq, ne, lt, le, ge, gt             |
| Numeric        | eq, ne, lt, le, ge, gt, in, notin  |

