# Source Definition

A Source Definition contains [Plug-in](/architecture/plug-in.md) or source specific data to be passed to the [Plug-in](/architecture/plug-in.md).

It always contains the address of the URL where the Plug-in can be reached.
In addition, it can contain authentication information which the Plug-in needs to connect to the data source.
[Plug-in](/architecture/plug-in.md) specific data (such as page length) or mapping between [Connector](/architecture/connector.md) and the [Plug-in](/architecture/plug-in.md) (such as a [Plug-in](/architecture/plug-in.md) classifies something as a parameter, but the Connector considers it a quantity) can also be part of the information.

Since a lot of the data is [provider](/architecture/provider.md)-specific, the [SourceDefinition](/specifications/formats/source-definition.md) can be extended with [Plug-in](/architecture/plug-in.md)-specific sections. 

The responsibility for that section is with the [Plug-in](/architecture/plug-in.md)-[provider](/architecture/provider.md) and to the [Connector](/architecture/connector.md)-[provider](/architecture/provider.md).
However, it is advised to share the specifications in a catalogue.

It conveys configuration information to a [Plug-in](/architecture/plug-in.md). 
Fixed elements are: [MapData](/specifications/formats/map-data.md), [AuthenticationData](/specifications/formats/authentication.md).
It can also specify [Plug-in](/architecture/plug-in.md) specific sections. In the example below, DdApiConfigurationSection contains such information.

```json
{
    "SourceDefinition": {
        "Id": 1,
        "Name": "WIS",
        "Code": "WIS",
        "Plugin": "DD-APIV2",
        "Url": "https://....",
        "AuthenticationData": {
            "AuthenticationType": 1,
            "ApiKeyData": {
                "ApiKey": "....",
                "ApiKeyHeader": "Ocp-Apim-Subscription-Key"
            }
         },
        "MapData": [
            {
                "CApiDataCategory": "Quantity",
                "CApiName": "Q",
                "SourceDataCategory": "Parameter",
                "SourceName": "Q"
            },
            {
                "CApiDataCategory": "Quantity",
                "CApiName": "GELDHD",
                "SourceDataCategory": "Parameter",
                "SourceName": "EGV"
            },
            {
                "CApiDataCategory": "Quantity",
                "CApiName": "WATHTE",
                "SourceDataCategory": "Parameter",
                "SourceName": "WATHTE"
            },
            {
                "CApiDataCategory": "Quantity",
                "CApiName": "NEERSG",
                "SourceDataCategory": "Parameter",
                "SourceName": "NEERSG"
            },
            {
                "CApiDataCategory": "Quantity",
                "CApiName": "KRUINHTE",
                "SourceDataCategory": "Parameter",
                "SourceName": "KRUINHTE"
            }
        ],
        "DdApiConfigurationSection": {
            "PageSize": 100,
            "SupportedQueryParameters": [
                "locationCode"
            ]
        }
    }
}
```