# DraftBitPlaid
Plaid x Draftbit

This is the project code we use used to integrate Plaid Link with Draftbit, which allows users to securely sign into their financial accounts and Plaid returns a public_token, which you can use to retreive their account information. 

First, you should be familiar with Plaid Link and have the relevant API keys and API calls setup - https://plaid.com/docs/link/

The way this works is: 
1. When the user wants to connect their account, we call the API to generate the public_token.
2. This is passed to the custom component.
3. When the user completes the process, we store the access_token as a variable. You'll need to call Plaid to exchange this for the permanent access_token.

1. Creating the public_token
![image](https://user-images.githubusercontent.com/15810675/144749431-5d23de7f-7b3e-4893-a75b-feecd7f04cac.png)

2. Passing it to the custom component
Secondly, you can paste the custom code text into your Draftbit Project.

Third, add the @burstware/expo-plaid-link package to your custom code packages. We're using version 1.0.5 (as of 11/30/2021) because the latest version is not rendering in expo.
![image](https://user-images.githubusercontent.com/15810675/144015499-ab73006c-8ba8-40e1-af7b-fd86d8588a97.png)

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

Lastly, this will route the user to a screen named 'Plaid Link 2'. You can change the name to any screen of your choice.
