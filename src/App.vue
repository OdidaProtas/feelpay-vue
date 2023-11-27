<template>
  <div class="dark:bg-gray-900 dark:text-white dark:text-white min-h-screen">
    <header class="pt-12">
      <div class="flex justify-center mb-3">
        <img
          class="w-64"
          src="https://res.cloudinary.com/dreamnerd/image/upload/v1686721359/feel-pay_yrvuwi.png"
          alt="FeelPay Full Logo"
        />
      </div>
      <h1 class="text-center text-4xl font-bold">
        FeelPay Angular Integration
      </h1>
      <p class="text-center text-3xl mt-3">
        An example of FeelPay integration into an Angular Placeholder
      </p>
      <div class="flex justify-center gap-3 mt-4 lg:px-64">
        <div>
          <a
            target="blank"
            class="underline text-blue"
            href="https://github.com/OdidaProtas/feelpay-vue"
            >Example Codebase</a
          >
        </div>
        <div>
          <a
            target="blank"
            class="underline text-blue"
            href="https://feelpay-docs.deno.dev/docs/frameworks/vuejs"
            >Vue Documentation</a
          >
        </div>
        <div>
          <a
            target="blank"
            class="underline text-blue"
            href="https://feelpay-docs.deno.dev/docs/intro/"
            >Full Documentation</a
          >
        </div>
      </div>
    </header>

    <div class="px-16 mt-4">
      <div id="dreamfeel-pay-button"></div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    // Load the external script
    const script = document.createElement("script");
    script.src = "https://feelpay.io/packages/v1";
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
        clientId: "4fc5d66d83186272",
        clientSecret: "27bf97cd8be3c608df90d24f3b7721ec",
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
