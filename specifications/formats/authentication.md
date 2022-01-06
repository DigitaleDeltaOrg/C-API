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
  "AuthenticationData": {
    "AuthenticationType": "ApiKey",
    "ApiKey": {
      "Key": "",
      "Header": ""
    }
  }
}
```

## OAUTH2 device flow
```json
{
  "AuthenticationData": {
    "AuthenticationType": "OAuthDeviceTokenRequest",
    "OAuthDeviceTokenRequest": {
      "Address": "",
      "DeviceCode": "",
      "GrantType": "",
      "ClientId": "",
      "ClientSecret": ""
    }
  }
}
```

## OAUTH2 client credentials flow
```json
{ 
  "AuthenticationData": {
    "AuthenticationType": "OAuthClientCredentialsTokenRequest",
    "OAuthClientCredentialsTokenRequest": {
      "Address": "",
      "GrantType": "",
      "ClientId": "",
      "ClientSecret": "",
      "Scope": ""
    }
  }
}
```

## OAUTH2 password flow
```json
{ 
  "AuthenticationData": {
    "AuthenticationType": "OAuthPasswordTokenRequest",
    "OAuthPasswordTokenRequest": {
      "Address": "",
      "GrantType": "",
      "ClientId": "",
      "ClientSecret": "",
      "Scope": "",
      "UserName": ""
    }
  }
}
```

## OAUTH2 authorization flow
```json
{ 
  "AuthenticationData": {
    "AuthenticationType": "OAuthAuthorizationCodeTokenRequest",
    "OAuthAuthorizationCodeTokenRequest": {
      "Address": "",
      "GrantType": "",
      "ClientId": "",
      "ClientSecret": "",
      "Scope": "",
      "RedirectUri": ""
    }
  }
}
```