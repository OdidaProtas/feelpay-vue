## Integrating with Vue.js

1. Create the feelpay checkout component


   ```javascript
   <template>
     <div>
       <!-- The container for the FeelPay button -->
       <div id="dreamfeel-pay-button"></div>
     </div>
   </template>

   <script>
   export default {
     mounted() {
       // Load the external script
       const script = document.createElement("script");
       script.src = "https://feelpay.vercel.app/packages/v1";
       script.async = true;
       script.onload = () => {
         // The script is loaded, initialize FeelPayWidget
         this.initializeFeelPay();
       };

       document.head.appendChild(script);
     },
     methods: {
       initializeFeelPay() {
         // After the script is loaded, you can use it here
         const orderDetails = {
           element: "dreamfeel-pay-button",
           clientId: "",
           clientSecret: "",
           description: "",
           order: {
             installments: 1,
             orderCompleteAfterInstallment: 1,
             vat: 16, // percentage
             amount: 3000,
             currency: "KES", //Only KES supported for now
             // Specify an array of order items.
             items: [
               {
                 id: "1",
                 name: "",
                 price: 0,
                 vat: 0,
                 url: ``,
                 image: "",
               },
             ],
           },
           onSuccess: (detail) => {
             // Handle success
             console.log(detail);
           },
           onError: (err) => {
             // Handle error
             console.log(err);
           },
           onInit: () => {},
           onUserCancel: () => {},
         };

         const feelpay = new window.FeelPayWidget(orderDetails);
         feelpay.init().then((pay) => {
           console.log(pay);
         });
       },
     },
   };
   </script>
   ```

2. ## Preparing transaction details

You must keep your CLIENT_ID and CLIENT_SECRET hidden with .env variables, specific to your plaform.

```javascript
const orderDetails = {
element: "dreamfeel-pay-button",
clientId: "YOUR_CLIENT_ID",
clientSecret: "YOUR_CLIENT_SECRET",
description:"",
order: {
 // Default for one time order checkout.
 installments: 1,
 orderCompleteAfterInstallment:1
 vat: 16, // percentage
 amount: 3000,
 currency:"KES",  //Only KES supported for now
 // Specify an array of order items.
 items: [
   {
     id: "1",
     name: "",
     price: 0,
     vat: 0,
     url: ``,
     image: "",
   },
 ],
},
onSuccess: (detail) => {
 // Handle success
 // const {feelPayCheckoutRequestID, feelPayCheckoutStatus, feelPayOrderId, ...} = detail
 console.log(detail);
},
onError: (err) => {
 // Handle error
 // {message:""}
 console.log(err);
},
// Run an action when innitialized!
onInit: () => {},
// Action when user cancels transaction!
onUserCancel: () => {},
};
```
4. A button will appear "Checkout with feelpay". When clicked, a popup appears, where user can complete transaction.
