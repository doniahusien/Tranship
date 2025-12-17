<template>
  <VeeField :name="name" v-slot="{ field, meta }">
    <div
      class="input_wrapper"
      :class="`${!meta.valid && meta.touched ? 'error' : ''} ${classes}`"
    >
      <label :for="id" class="label" v-if="label">{{ label }}</label>

      <textarea
        :rows="rows"
        :id="id"
        v-bind="field"
        :placeholder="placeholder"
        class="font-light "
        :class="
          !meta.valid &&
          meta.touched &&
          'border-error placeholder:text-error lg:text-lg min-h-30 resize-none'
        "
      />
<!-- 
      <VeeErrorMessage
        v-if="!meta.valid && meta.touched"
        :name="name"
        as="div"
        class="text-error text-sm"
      /> -->
    </div>
  </VeeField>
</template>

<script setup>
defineProps({
  id: {
    required: false,
  },
  name: {
    required: true,
  },
  label: {
    required: false,
  },
  rows: {
    required: false,
  },
  classes: {
    required: false,
  },
  placeholder: {
    required: true,
  },
});
</script>
