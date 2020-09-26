<template>
  <div class="card">
    <slot name="title">
      <div class="text-xl font-medium mb-6">{{ title }}</div>
    </slot>
    <slot />
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    title: {
      default: '',
      required: false,
    },
  },
}
</script>

<style lang="postcss">
.card {
  @apply bg-white shadow-md px-12 py-6 w-full rounded-lg;
}
</style>
