<template>
  <div class="py-16 px-4 overflow-hidden sm:px-6 lg:px-8 lg:py-24 bg-gray-100">
    <NuxtLink to="/" class="text-yellow-500"> &#60; Go to Home</NuxtLink>
    <div class="max-w-xl mx-auto">
      <!-- This example requires Tailwind CSS v2.0+ -->
      <div class="rounded-md bg-blue-50 p-4 my-5">
        <div class="flex">
          <div class="flex-shrink-0">
            <!-- Heroicon name: solid/x-circle -->
            <svg
              class="h-5 w-5 text-blue-400"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
              fill="currentColor"
              aria-hidden="true"
            >
              <path
                fill-rule="evenodd"
                d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.707 7.293a1 1 0 00-1.414 1.414L8.586 10l-1.293 1.293a1 1 0 101.414 1.414L10 11.414l1.293 1.293a1 1 0 001.414-1.414L11.414 10l1.293-1.293a1 1 0 00-1.414-1.414L10 8.586 8.707 7.293z"
                clip-rule="evenodd"
              />
            </svg>
          </div>
          <div class="ml-3">
            <h3 class="text-sm font-medium text-blue-800">
              How to trigger the behaviour
            </h3>
            <div class="mt-2 text-sm text-blue-700">
              <ul class="list-disc pl-5 space-y-1">
                <li>
                  If you load the /contact page, then the "agree" button doesn't
                  work.
                </li>
                <li>
                  If you come from the <code>/</code> landpage, and then you go
                  to <code>/contact</code> then the button works, but when you
                  submit you receive an strange error
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <div class="text-center">
        <h2 class="text-4xl leading-6 font-medium text-gray-900">
          Contact me
        </h2>
      </div>
      <div class="mt-12">
        <form
          name="contactme"
          method="POST"
          class="grid grid-cols-1 gap-y-6 sm:grid-cols-2 sm:gap-x-8"
          @submit.prevent="onSubmit"
        >
          <p class="hidden">
            <label
              >Don’t fill this out if you’re human: <input name="bot-field"
            /></label>
          </p>
          <div class="sm:col-span-2">
            <label for="name" class="block text-sm font-medium text-gray-700"
              >Name</label
            >
            <div class="mt-1">
              <input
                v-model="name"
                type="text"
                name="name"
                id="name"
                autocomplete="given-name"
                placeholder="John Doe"
                class="py-3 px-4 block w-full shadow-sm focus:ring-yellow-500 focus:border-yellow-500 border-gray-300 rounded-md"
              />
            </div>
          </div>
          <div class="sm:col-span-2">
            <label for="message" class="block text-sm font-medium text-gray-700"
              >Message</label
            >
            <div class="mt-1">
              <textarea
                v-model="message"
                id="message"
                name="message"
                rows="4"
                placeholder="Your message here..."
                class="py-3 px-4 block w-full shadow-sm focus:ring-yellow-500 focus:border-yellow-500 border-gray-300 rounded-md"
              ></textarea>
            </div>
          </div>
          <div class="sm:col-span-2">
            <div class="flex items-start">
              <div class="flex-shrink-0">
                <!-- Enabled: "bg-yellow-600", Not Enabled: "bg-gray-200" -->
                <button
                  @click="toggleAgree()"
                  type="button"
                  v-bind:class="{
                    'bg-yellow-600': agreed,
                    'bg-gray-200': !agreed
                  }"
                  class="relative inline-flex flex-shrink-0 h-6 w-11 border-2 border-transparent rounded-full cursor-pointer transition-colors ease-in-out duration-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-yellow-500"
                  aria-pressed="false"
                >
                  <span class="sr-only">Agree</span>
                  <!-- Enabled: "translate-x-5", Not Enabled: "translate-x-0" -->
                  <span
                    v-bind:class="{
                      'translate-x-5': agreed,
                      'translate-x-0': !agreed
                    }"
                    aria-hidden="true"
                    class="translate-x-0 inline-block h-5 w-5 rounded-full bg-white shadow transform ring-0 transition ease-in-out duration-200"
                  ></span>
                </button>
              </div>
              <div class="ml-3">
                <p class="text-base text-gray-500">
                  By selecting this, I understand that this form is storing my
                  submitted information so I can be contacted.
                </p>
              </div>
            </div>
          </div>
          <div class="sm:col-span-2">
            <button
              :disabled="completed"
              type="submit"
              v-bind:class="{ 'cursor-not-allowed opacity-50': completed }"
              class="w-full inline-flex items-center justify-center px-6 py-3 border border-transparent rounded-md shadow-sm text-base font-medium text-white bg-yellow-600 hover:bg-yellow-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-yellow-500"
            >
              Let's talk
            </button>
          </div>
        </form>
      </div>
      <div class="relative mt-10">
        <div class="absolute inset-0 flex items-center" aria-hidden="true">
          <div class="w-full border-t border-gray-300"></div>
        </div>
        <div class="relative flex justify-center">
          <span class="px-2 bg-gray-100 text-sm text-gray-500">
            OR
          </span>
        </div>
      </div>
      <div class="mt-5 text-gray-500 flex flex-inline justify-center">
        <a href="https://twitter.com/aleixmorgadas" target="__blank">
          <span>Feel free to drop me a</span>
          <span class="text-blue-500 mx-1">tweet</span>
          <img src="/technologies/twitter.jpg" class="h-5 w-5 inline" />
        </a>
      </div>
    </div>
  </div>
</template>
<script>
function encode(data) {
  return Object.keys(data)
    .map(key => encodeURIComponent(key) + "=" + encodeURIComponent(data[key]))
    .join("&");
}

export default {
  data: function() {
    return {
      name: "",
      message: "",
      agreed: false
    };
  },
  methods: {
    toggleAgree: function() {
      this.agreed = !this.agreed;
    },
    onSubmit: function(event) {
      event.preventDefault();
      fetch("/", {
        method: "POST",
        headers: { "Content-Type": "application/x-www-form-urlencoded" },
        body: encode({
          "form-name": event.target.getAttribute("name"),
          name: this.name,
          message: this.message,
          agreed: this.agreed
        })
      })
        .then(() => this.$router.push({ path: "/success-form" }))
        .catch(error => alert(error));
    }
  },
  computed: {
    completed: function() {
      return this.name === "" || this.message === "" || !this.agreed;
    }
  }
};
</script>
