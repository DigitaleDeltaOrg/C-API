# DataBody

The DataBody contains all information send to the plug-in: the query, the mappings, the plug-in specific data (if needed), etc.

It has the following structure:

## Properties
| Name                  | Type                                                                            | Remarks                                                                                                                                                    |
|-----------------------|---------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| sourceDefinition      | [SourceDefinition](/specifications/formats/source-definition.md)                | Describes data for the Source                                                                                                                              |
| conditions            | Array of [Condition](/specifications/formats/condition.md)                      | Describes the filter                                                                                                                                       |
| connectorCapabilities | Array of [ConnectorCapability](/specifications/formats/connector-capability.md) | Describes the capabilities that the [connector](/architecture/connector.md) knows                                                                          |
| responseId            | [StringType](/specifications/formats/data-type.md)                              | Identifier that the [plug-in](/architecture/plug-in.md) must return as part of the [measurement response](/specifications/formats/measurement-response.md) |


```json
{
  "sourceDefinition": {},
  "conditions": {},
  "connectorCapabilities":{},
  "responseId": ""
}
```
