# DraftBitPlaid
Plaid x Draftbit

This is the project code we use used to integrate Plaid Link with Draftbit, which allows users to securely sign into their financial accounts and Plaid returns a public_token, which you can use to retreive their account information. 

For reference, Plaid maintains a [React Native repo](https://github.com/plaid/react-native-plaid-link-sdk), but it isn't Expo compatible. For this, we use [Burstware Expo Plaid Link](https://github.com/burstware/expo-plaid-link)

## How Plaid Link in Draftbit works
1. When the user wants to connect their account, we call the Plaid API to generate the public_token.
2. This is passed to the custom component via a stored variable.
3. When the user completes the Plaid Link process, it returns an access_token which we store as a variable.

### Creating the public_token
We used a button asking the user if they want to link more accounts. This calls the Plaid API returning the public_token
![image](https://user-images.githubusercontent.com/15810675/144749431-5d23de7f-7b3e-4893-a75b-feecd7f04cac.png)

### Passing the public_token to the custom code
First, @burstware/expo-plaid-link package to your custom code packages. 

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

The code provided in this repo references the variables above. The only change you need is the onSuccess page route.
