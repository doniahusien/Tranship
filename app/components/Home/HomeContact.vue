<script setup lang="ts">
import { Form as VeeForm } from "vee-validate";
import * as yup from "yup";

const schema = yup.object({
  name: yup.string().required("Name is required"),
  email: yup.string().email("Invalid email").required("Email is required"),
 /*  phone: yup.string().required("Phone is required"),
  interest: yup.string().required("Please select a service"), */
  message: yup.string().required("Message is required"),
});

const handleSubmit = (values: any) => {
  console.log(values);
};
</script>

<template>
  <section class="bg-semi-white py-5 lg:p-0 ">
<div class="container mx-auto grid grid-cols-1 md:grid-cols-2">
    <div class="hidden relative max-w-xl  md:flex items-center  overflow-hidden">
    <NuxtImg
      src="/images/contactbg.png"
      alt="Contact"
      class="
      w-full
      h-auto
        object-contain
        object-left
      "
    />
  </div>
    <div class="flex flex-col justify-center md:px-10">
      <h2 class="text-secondary text-3xl font-semibold mb-4 uppercase">
        Quick quote
      </h2>

      <p class="mb-8 text-gray-600 max-w-xl">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
      </p>

      <VeeForm
        :validation-schema="schema"
        @submit="handleSubmit"
        class="space-y-5 max-w-xl"
      >
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <inputsBase name="name" placeholder="Name *" />
          <inputsBase name="email" type="email" placeholder="Email *" />
        </div>

        <div class="grid  grid-cols-1 md:grid-cols-2 gap-4">
          <inputsBase name="phone" placeholder="Phone" />
          <inputsBase name="interest" placeholder="Interest of Service" />
        </div>

        <inputsTextarea
          name="message"
          placeholder="Message *"
          rows="5"
        />

        <button
          type="submit"
          class="bg-secondary text-white px-8 py-3 rounded-md uppercase"
        >
          Submit
        </button>
      </VeeForm>
    </div>
</div>
  </section>


</template>
<style scoped>

</style>

