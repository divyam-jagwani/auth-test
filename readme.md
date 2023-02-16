This sample is used to successfully logout of AADB2C provider when logging out of SWA.

## Configuration
1. Go to the App registration in your AAD B2C tenant which is used for the SWA Auth.
2. In the `Authentication` tab, under the Front-channel Logout URL, specify the SWA logout endpoint
![image](https://user-images.githubusercontent.com/6436807/219319845-97e12a80-9945-45f1-92da-56673533b530.png)
3. Go to the openid configuration endpoint of your AAD B2C app.This can be found in `staticwebapp.config.json` as well under `wellKnownOpenIdConfiguration` field as you already configured this.
4. Get the `end_session_endpoint` value which will act as the logout url
5. Add the `post_logout_redirect_uri` query parameter pointing to the SWA logout endpoint and construct the full url whcih would look something like `https://vijilla.b2clogin.com/vijilla.onmicrosoft.com/b2c_1_susi/oauth2/v2.0/logout?post_logout_redirect_uri=https%3A%2F%2Fpolite-mushroom-0346f2a10.2.azurestaticapps.net%2F.auth%2Flogout`
6. Take the user to this url when they click on logout action. 
7. This should take care of logging the user out of the provider and then from the SWA app.
8. And based on the rules configured, it will take the user back to the login page.
