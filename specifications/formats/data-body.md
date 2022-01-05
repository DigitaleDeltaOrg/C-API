# DataBody

The DataBody contains all information send to the plug-in: the query, the mappings, the plug-in specific data (if needed), etc.

It has the following structure:

```json
{
  "SourceDefinition": {},
  "Conditions": {},
  "ConnectorCapabilities":{},
  "ResponseId": ""
}
```

The definitions of [SourceDefinition](/specifications/formats/source-definition.md), [Conditions](/specifications/formats/condition.md) and [ConnectorCapabilities](/specifications/formats/connector-capability.md) can be found in their own sections.
ResponseId is a value passed by the Connector, to keep track of which request produced which response.
It is required that the plug-in returns the ResponseId to the Connector as part of the ResponseCache.
