<template>
  <div>
    <div class="mb-2" :class="{ 'text-xl font-medium': boldLabel }">
      {{ label }}
    </div>
    <slot name="content" />
    <input
      class="form-input mb-6"
      type="text"
      :value="value"
      :placeholder="placeholder"
      @input="$emit('input', $event.target.value)"
      @keyup.enter="$emit('enter')"
    />
  </div>
</template>

<script>
export default {
  name: 'FormInput',
  props: {
    value: {
      type: String,
      required: true,
    },
    label: {
      type: String,
      required: false,
      default: '',
    },
    placeholder: {
      type: String,
      required: false,
      default: '',
    },
    boldLabel: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
}
</script>

<style lang="postcss">
.form-input {
  @apply border border-gray-300 rounded-lg px-3 py-2 w-full transition duration-200;
}
.form-input:hover {
  @apply border-gray-500;
}
.form-input:focus {
  @apply border-orange-400;
  outline: 0;
}
.bold-label {
  @apply text-xl font-medium mb-2;
}
</style>
