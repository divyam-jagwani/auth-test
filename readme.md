This site has an issue where when you logout of the app, it automatically logs you back in.
Example: https://jolly-meadow-09a103c10.2.azurestaticapps.net

There are two approaches on how to unblock here:

1. Modifying the swa config to expose one endpoint for anonymous access. More details and sample code at https://github.com/vivekjilla/auth-test/tree/aadb2c
2. Logging the user out of AAD B2C provider (incase they use it) before logging out of SWA. More details and sample code at https://github.com/vivekjilla/auth-test/tree/blank_login
