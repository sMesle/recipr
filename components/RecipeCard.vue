<template>
  <div class="recipe-card">
    <img class="recipe-card-img" :src="recipe.imgLink" />
    <div class="p-4">
      <span class="text-bold text-xl">{{ recipe.name }}</span>
      <div class="text-xs">Ajouté par {{ recipe.addedBy }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RecipeCard',
  props: {
    recipe: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style lang="postcss">
.recipe-card {
  @apply transition duration-200 ease-in-out bg-white shadow-md rounded-lg;
}
.recipe-card:hover {
  transform: scale(1.025);
}
.recipe-card-img {
  @apply w-full rounded-tl-lg rounded-tr-lg object-cover;
  height: 299px;
  max-height: 299px;
}
</style>
