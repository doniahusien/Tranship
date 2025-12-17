<template>
  <VeeField :type="type" :name="name" v-slot="{ field, meta }">
    <div
      class="input_wrapper"
      :class="(
        !meta.valid && meta.touched ? 'error':'',
        classes)
      "
    >
      <label :for="id" class="label" v-if="label">{{ label }}</label>
      <input
        :type="type"
        :id="id"
        :accept="accept"
        v-bind="field"
        :placeholder="placeholder"
        :class="
          !meta.valid &&
          meta.touched &&
          'border-secondary  placeholder:text-secondary  error'
        "
        @change="emit('change', $event)"
      />
<!-- 
      <VeeErrorMessage
        v-if="!meta.valid && meta.touched"
        :name="name"
        as="div"
        class="error"
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
  placeholder: {
    required: true,
  },
  classes: {
    required: false,
  },
  accept: {
    required: false,
  },
  type: {
    required: false,
    default: "text",
  },
});
const emit = defineEmits(["change"]);
</script>

<style scoped>

</style>
