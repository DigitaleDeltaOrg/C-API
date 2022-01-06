# DataBody

The DataBody contains all information send to the plug-in: the query, the mappings, the plug-in specific data (if needed), etc.

It has the following structure:

## Properties
| Name                  | Type                                                                            | Remarks                                                                                                                                                    |
|-----------------------|---------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SourceDefinition      | [SourceDefinition](/specifications/formats/source-definition.md)                | Describes data for the Source                                                                                                                              |
| Conditions            | Array of [Condition](/specifications/formats/condition.md)                      | Describes the filter                                                                                                                                       |
| ConnectorCapabilities | Array of [ConnectorCapability](/specifications/formats/connector-capability.md) | Describes the capabilities that the [connector](/architecture/connector.md) knows                                                                          |
| ResponseId            | [StringType](/specifications/formats/data-type.md)                              | Identifier that the [plug-in](/architecture/plug-in.md) must return as part of the [measurement response](/specifications/formats/measurement-response.md) |


```json
{
  "SourceDefinition": {},
  "Conditions": {},
  "ConnectorCapabilities":{},
  "ResponseId": ""
}
```
