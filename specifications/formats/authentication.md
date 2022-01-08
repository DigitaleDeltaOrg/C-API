# Authentication

Not all data is free, or freely accessible.

To allow some kind of authentication, the C-API allows the following methods:

- OAUTH2 (includes OpenID Connect)
- API-keys

Authentication information is passed from the [Connector](/architecture/connector.md) to the [Plug-in](/architecture/plug-in.md). 
The data for the different OAUTH2 flows conform to the [Identity Model definition](https://identitymodel.readthedocs.io/en/latest/)

All properties are [StringType](/specifications/formats/data-type.md#data-types).

## API-keys
```json
{ 
  "authenticationData": {
    "authenticationType": "ApiKey",
    "apiKey": {
      "Key": "",
      "Header": ""
    }
  }
}
```

## OAUTH2 device flow
```json
{
  "authenticationData": {
    "authenticationType": "OAuthDeviceTokenRequest",
    "oAuthDeviceTokenRequest": {
      "address": "",
      "deviceCode": "",
      "grantType": "",
      "clientId": "",
      "clientSecret": ""
    }
  }
}
```

## OAUTH2 client credentials flow
```json
{ 
  "authenticationData": {
    "authenticationType": "OAuthClientCredentialsTokenRequest",
    "oAuthClientCredentialsTokenRequest": {
      "address": "",
      "grantType": "",
      "clientId": "",
      "clientSecret": "",
      "scope": "",
    }
  }
}
```

## OAUTH2 password flow
```json
{ 
  "authenticationData": {
    "authenticationType": "OAuthPasswordTokenRequest",
    "oAuthPasswordTokenRequest": {
      "address": "",
      "grantType": "",
      "clientId": "",
      "clientSecret": "",
      "scope": "",
      "userName": ""
    }
  }
}
```

## OAUTH2 authorization flow
```json
{ 
  "authenticationData": {
    "authenticationType": "OAuthAuthorizationCodeTokenRequest",
    "oAuthAuthorizationCodeTokenRequest": {
      "address": "",
      "grantType": "",
      "clientId": "",
      "clientSecret": "",
      "scope": "",
      "redirectUri": ""
    }
  }
}
```