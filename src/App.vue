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
      <h1 class="text-center text-4xl font-bold">FeelPay Vue Integration</h1>
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

    <section>
      <feelpay-launcher
        clientSecret="0a7013c0fac16ea352b45cd5b52534bd"
        clientKey="e07fea12a51701c1"
        order="{}"
      />
    </section>
  </div>
</template>

