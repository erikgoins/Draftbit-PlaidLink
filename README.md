# DraftBitPlaid
Plaid x Draftbit

This is the project code we use used to integrate Plaid Link with Draftbit, which allows users to securely sign into their financial accounts and Plaid returns a public_token, which you can use to retreive their account information. 

First, you should be familiar with Plaid Link and have the relevant API keys and API calls setup - https://plaid.com/docs/link/

Secondly, you can paste the custom code into your Draftbit Project

Additionally, you need the following:

**Device Variables**
![image](https://user-images.githubusercontent.com/15810675/144014596-d02d402c-828e-4535-b2d6-452586d96b19.png)

**App Variables**
![image](https://user-images.githubusercontent.com/15810675/144014658-c127c44a-3a5a-448e-a067-723318dd1d11.png)

And a **Custom Code Component** of:
<CustomCode.ExpoPlaidLink 
LinkToken = {props.route?.params?.LinkToken}
navigation={props.navigation}
/>

To integrate this, when the user wants to connect their account, we call the API to generate the public_token.
This is passed to the custom component.
When the user completes the process, we store the access_token as a variable. You'll need to call Plaid to exchange this for the permanent access_token.
