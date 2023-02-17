## Using facebook as auth provider

Please follow these docs to setup Facebook as provider: https://learn.microsoft.com/en-us/azure/static-web-apps/authentication-custom?tabs=facebook%2Cinvitations#configure-a-custom-identity-provider

### While logging in to app, if you see the 403 error, it's possible that we're not receiving email claim from the fb. 

There are two ways to solve this:
1. Add `email` scopes to start receiving the email id, as below.

```diff
{
  "auth": {
    "identityProviders": {
      "facebook": {
        "registration": {
          "appIdSettingName": "FACEBOOK_APP_ID",
          "appSecretSettingName": "FACEBOOK_APP_SECRET"
        },
+      "login": {
+         "scopes":["email"]
+       }    
      }
    }
  }
}
```

2. Change the claim we are checking for to get user details, by adding userDetailsClaim pointing to `nameidentifier`, as below.
This is useful in case someone doesn't have a valid email id as well.

```diff
{
  "auth": {
    "identityProviders": {
      "facebook": {
        "registration": {
          "appIdSettingName": "FACEBOOK_APP_ID",
          "appSecretSettingName": "FACEBOOK_APP_SECRET"
        },
+       "userDetailsClaim": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier"
      }
    }
  }
}
```
