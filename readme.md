This sample is used to demonstrate successfully logging out of AADB2C provider as well when logging out of SWA.

## Prerequisites 
- AAD B2C provider is already setup and integrated with your SWA App. Steps on how to do this can be found at https://learn.microsoft.com/en-us/azure/active-directory-b2c/configure-authentication-in-azure-static-app

## Logout configuration
1. Go to the App registration in your AAD B2C tenant which is used for the SWA Auth.
2. In the `Authentication` tab, under the Front-channel Logout URL, specify the SWA logout endpoint
![image](https://user-images.githubusercontent.com/6436807/219319845-97e12a80-9945-45f1-92da-56673533b530.png)
3. Open the openid configuration endpoint of your AAD B2C app in the browser. This can be found in `staticwebapp.config.json` as well, under `wellKnownOpenIdConfiguration` field as you already configured this as part of prerequisites.
4. Get the `end_session_endpoint` value which will act as the logout url
5. Add the `post_logout_redirect_uri` query parameter pointing to the SWA logout endpoint to this url and construct the full url which would look something like `https://vijilla.b2clogin.com/vijilla.onmicrosoft.com/b2c_1_susi/oauth2/v2.0/logout?post_logout_redirect_uri=https%3A%2F%2Fpolite-mushroom-0346f2a10.2.azurestaticapps.net%2F.auth%2Flogout`
6. Take the user to this url when they click on logout action like demonstrated in `index.html` file in this repo. 
7. This should take care of logging the user out of the provider and then from the SWA app.
8. And based on the routing rules configured, it will take the user back to the login page.

## Testing
- This repo has the sample code which does the above steps.
- Endpoint to test this scenario out: https://polite-mushroom-0346f2a10.2.azurestaticapps.net/
