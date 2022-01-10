# Source Definition

A Source Definition contains [Plug-in](/architecture/plug-in.md) or source specific data to be passed to the [Plug-in](/architecture/plug-in.md).

It always contains the address of the URL where the Plug-in can be reached.
In addition, it can contain authentication information which the Plug-in needs to connect to the data source.
[Plug-in](/architecture/plug-in.md) specific data (such as page length) or mapping between [Connector](/architecture/connector.md) and the [Plug-in](/architecture/plug-in.md) (such as a [Plug-in](/architecture/plug-in.md) classifies something as a parameter, but the Connector considers it a quantity) can also be part of the information.

Since a lot of the data is [provider](/architecture/provider.md)-specific, the [SourceDefinition](/specifications/formats/source-definition.md) can be extended with [Plug-in](/architecture/plug-in.md)-specific sections. 

The responsibility for that section is with the [Plug-in](/architecture/plug-in.md)-[provider](/architecture/provider.md) and to the [Connector](/architecture/connector.md)-[provider](/architecture/provider.md).
However, it is advised to share the specifications in a catalogue.

It conveys configuration information to a [Plug-in](/architecture/plug-in.md). 

## Properties
| Name               | Type                                                            | Remarks                                                                                                                       |
|--------------------|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| name               | [StringType](/specifications/formats/data-type.md)              | Name of the [Source](/architecture/data-source.md)                                                                            | 
| code               | [StringType](/specifications/formats/data-type.md)              | Code of the [Source](/architecture/data-source.md)                                                                            |
| plugin             | [StringType](/specifications/formats/data-type.md)              | Type of the [Plug-in](/architecture/plug-in.md)                                                                               |
| url                | [StringType](/specifications/formats/data-type.md)              | HTTPS address of the [Plug-in](/architecture/plug-in.md)                                                                      |
| authenticationData | [AuthenticationData](/specifications/formats/authentication.md) | Information required for the [Plug-in](/architecture/plug-in.md) to [authenticate](/specifications/formats/authentication.md) |
| mapData            | [MapData](/specifications/formats/map-data.md)                  | Information required to map data between [Connector](/architecture/connector.md) and [Plug-in](/architecture/plug-in.md)      |


It can also specify [Plug-in](/architecture/plug-in.md) specific sections. In the example below, DdApiConfigurationSection contains such information.

```json
{
    "sourceDefinition": {
        "name": "WIS",
        "code": "WIS",
        "plugin": "DD-APIV2",
        "url": "https://....",
        "authenticationData": {
            "authenticationType": 1,
            "apiKeyData": {
                "key": "....",
                "header": "Ocp-Apim-Subscription-Key"
            }
         },
        "mapData": [
            {
                "cApiDataCategory": "Quantity",
                "cApiName": "Q",
                "sourceDataCategory": "Parameter",
                "sourceName": "Q"
            },
            {
                "cApiDataCategory": "Quantity",
                "cApiName": "GELDHD",
                "sourceDataCategory": "Parameter",
                "sourceName": "EGV"
            },
            {
                "cApiDataCategory": "Quantity",
                "cApiName": "WATHTE",
                "sourceDataCategory": "Parameter",
                "sourceName": "WATHTE"
            },
            {
                "cApiDataCategory": "Quantity",
                "cApiName": "NEERSG",
                "sourceDataCategory": "Parameter",
                "sourceName": "NEERSG"
            },
            {
                "cApiDataCategory": "Quantity",
                "cApiName": "KRUINHTE",
                "sourceDataCategory": "Parameter",
                "sourceName": "KRUINHTE"
            }
        ],
        "ddApiConfigurationSection": {
            "pageSize": 100,
            "supportedQueryParameters": [
                "locationCode"
            ]
        }
    }
}
```