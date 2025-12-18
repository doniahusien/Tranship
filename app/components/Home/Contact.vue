<script setup lang="ts">
import { Form as VeeForm } from "vee-validate";
import * as yup from "yup";
const {t,locale} = useI18n();
const isRTL = computed(() => locale.value === 'ar')
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
  <section class="bg-semi-white py-5 px-2 lg:p-0 ">
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
      :class="[isRTL? 'scale-x-[-1]' : '']"
    />
  </div>
    <div class="flex flex-col justify-center md:px-10">
      <h2 class="text-secondary text-xl md:text-3xl font-semibold mb-4 uppercase">
        {{$t('TITLES.GET_QUOTE')}}
      </h2>

      <p class="mb-8 text-base md:text-xl text-gray-600 max-w-xl">
        {{$t('LABELS.GENERAL_DESC')}}
      </p>

      <VeeForm
        :validation-schema="schema"
        @submit="handleSubmit"
        class="space-y-5 max-w-xl"
      >
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <inputsBase name="name" :placeholder="$t('TITLES.name')" />
          <inputsBase name="email" type="email" :placeholder="$t('TITLES.email')"  />
        </div>

        <div class="grid  grid-cols-1 md:grid-cols-2 gap-4">
          <inputsBase name="phone" :placeholder="$t('TITLES.phone')"  />
          <inputsBase name="interest" :placeholder="$t('TITLES.interest')"  />
        </div>

        <inputsTextarea
          name="message"
         :placeholder="$t('TITLES.message')" 
          rows="5"
        />

        <button
        aria-label="submit contact form"
          type="submit"
          class="bg-secondary text-white px-8 py-3 rounded-md uppercase"
        >
          {{$t('BUTTONS.SUBMIT')}}
        </button>
      </VeeForm>
    </div>
</div>
  </section>


</template>
<style scoped>

</style>

