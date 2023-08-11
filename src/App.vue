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
        clientId: "afc17c43531c2441",
        clientSecret: "67d6bc1a5843172286ce6ca701f80094",
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
