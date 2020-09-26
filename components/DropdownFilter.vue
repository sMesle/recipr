<template>
  <div>
    <button class="btn btn-orange block border-0 ml-6" @click="open = !open">
      Filtres
    </button>
    <div v-show="open" class="z-10 absolute bg-white shadow-xl rounded-lg p-6">
      <!-- A transformer en slot -->
      <slot name="content" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'DropdownFilter',
  props: {
    open: {
      type: Boolean,
      required: true,
    },
  },
}
</script>

<style lang="postcss">
.btn {
  @apply inline-block font-bold rounded-lg px-4 py-2 transition-colors duration-200;
}
.btn-orange {
  @apply bg-orange-400 text-white;
}
.btn-orange:hover {
  @apply bg-orange-500;
}
.btn-filter {
  @apply w-24 border-solid border border-orange-400 bg-orange-100 text-orange-400 rounded-md;
}
</style>
