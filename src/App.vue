<template>
  <header>
    <nav class="bg-[#162447] p-4">
    <div class="container mx-auto flex justify-between items-center">
      <div class="text-white text-2xl font-bold">Finsweet</div>
      <ul class="flex space-x-4">
        <li><a href="#" class="text-white hover:text-gray-300">Home</a></li>
        <li><a href="#" class="text-white hover:text-gray-300">About</a></li>
        <li><a href="#" class="text-white hover:text-gray-300">Pricing</a></li>
        <li><a href="#" class="text-white hover:text-gray-300">Blog</a></li>
        <li>
          <router-link to="/contact" class="bg-white text-[#162447] py-2 px-4 rounded-md hover:bg-gray-200">
            Contacts
          </router-link>
        </li>
      </ul>
    </div>
  </nav>
    <div class="container mx-auto p-6">
      <h2 class="text-2xl font-bold mb-4">Lets Talk!</h2>
      <form
        @submit.prevent="handleSubmit"
        class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4"
      >
        <div class="mb-4">
          <label for="name" class="block text-gray-700 text-sm font-bold mb-2"
            >Name</label
          >
          <input
            type="text"
            v-model="formData.name"
            id="name"
            required
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          />
        </div>
        <div class="mb-4">
          <label for="email" class="block text-gray-700 text-sm font-bold mb-2"
            >Email</label>
          <input
            type="email"
            v-model="formData.email"
            id="email"
            required
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"/>
        </div>
        <div class="mb-4">
          <label
            for="message"
            class="block text-gray-700 text-sm font-bold mb-2"
            >Message</label
          >
          <textarea
            v-model="formData.message"
            id="message"
            required
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          ></textarea>
        </div>
        <div class="mb-4">
          <button
            type="submit"
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          >
            Send Message
          </button>
        </div>
      </form>
    </div>
<section class="bg-[#162447] text-white py-10 flex">
    <div class="container mx-auto flex flex-col md:flex-row justify-between items-center px-4">
      <div class="mb-6 md:mb-0">
        <h2 class="text-3xl font-bold">Finsweet</h2>
        <p class="mt-2">We are always open to discuss your project and improve your online presence.</p>
        <div class="mt-4">
          <a href="mailto:contact@website.com" class="bg-yellow-500 text-black py-2 px-4 rounded hover:bg-yellow-400">
            Email me at
          </a>
          <span class="ml-2">contact@website.com</span>
        </div>
        <div class="mt-2">
          <a href="tel:9027627895" class="text-yellow-500 hover:underline">
            Call us: 902 762 7895
          </a>
        </div>
      </div>
      <div class="text-center md:text-right">
        <h3 class="text-xl font-semibold">Lets Talk!</h3>
        <p class="mt-2">We are always open to discuss your project, improve your online presence, and help with your UI/UX design challenges.</p>
        <div class="flex justify-center md:justify-end mt-4 space-x-4">
          <a href="#" class="text-yellow-500 hover:underline"><img src="./img/facebook.svg" alt="facebook"></a>
          <a href="#" class="text-yellow-500 hover:underline"><img src="./img/linkidIn.svg" alt="linkidIn"></a>
          <a href="#" class="text-yellow-500 hover:underline"><img src="./img/instagram.svg" alt="instagram"></a>
          <a href="#" class="text-yellow-500 hover:underline"><img src="./img/twitter.svg" alt="twitter"></a>
        </div>
      </div>
    </div>
  </section>
  </header>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "ContactForm",
  setup() {
    const formData = ref({
      name: "",
      email: "",
      message: "",
    });

    const handleSubmit = async () => {
      try {
        console.log("Form submitted:", formData.value);
        const response = await fetch('https://api.example.com/contact', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(formData.value),
        });
        if(!response.ok) {
          throw new Error('Network responce was not ok');
        }

        const result = await response.json();
        console.log(result);
        
        formData.value = {name: '', email: '', message: ''};
        alert('Message sent successfully!');
      } catch (error) {
        console.error('Error submitting form:', error);
        alert('Faild to send message. Please try again later.');
      }
    };

    return {
      formData,
      handleSubmit,
    };
  },
});
</script>

<style scoped>
/* Qo'shimcha uslublar */
</style>


