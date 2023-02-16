This sample is used to demonstrate how to not log back in to the swa by restricting anonymous access to the entire application exception for one endpoint.

- You can expose one endpoint for anonymous users and redirect the user to this endpoint in case they're not logged in.
- And in this anonymous endpoint, you can add a simple login button to log the users back in to your site

Your swa config would look something like this:
```json
{
  "routes": [
    {
      "route": "/login",
      "allowedRoles": ["anonymous"]
    },
    {
      "route": "/*",
      "allowedRoles": ["authenticated"]
    }
  ],
  "responseOverrides": {
    "401": {
      "statusCode": 302,
      "redirect": "/login"
    }
  }
}
```

And this repo contains the sample site which is using this config. you can look at login.html and index.html to understand this issue in better details.
Sample endpoint to try this out: https://icy-desert-01df51b10.2.azurestaticapps.net/
