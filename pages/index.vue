<template>
  <div class="relative">
    <div>
      <div class="flex justify-center mb-12">
        <input
          v-model="search"
          class="search-input w-1/2"
          placeholder="Rechercher une recette"
        />
        <dropdown-filter :open="dropdownFilter">
          <template v-slot:content>
            <div class="flex justify-center mb-2 text-gray-400 font-bold">
              Sélection de filtre
            </div>
            <div class="mb-2">
              <span class="text-orange-400 font-bold">Catégories</span>
            </div>
            <div class="flex flex-wrap">
              <!-- List de filtre -->
              <button class="btn-filter p-4 mb-4 mr-4">Salade</button>
              <button class="btn-filter p-4 mb-4 mr-4">Dessert</button>
              <button class="btn-filter p-4 mb-4 mr-4">Plat</button>
              <button class="btn-filter p-4 mb-4 mr-4">Entrée</button>
              <button class="btn-filter p-4 mb-4 mr-4">Soupe</button>
            </div>
          </template>
        </dropdown-filter>
      </div>
      <transition-group name="list" tag="div" class="grid grid-cols-5 gap-12">
        <recipe-card
          v-for="(recipe, i) in recipesFiltered"
          :key="i"
          :recipe="recipe"
        >
        </recipe-card>
      </transition-group>
    </div>
    <div class="fixed-bottom-right">
      <nuxt-link to="/recipe/creation">
        <button class="btn-circle btn-orange shadow-md">
          <font-awesome-icon icon="plus" />
        </button>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import RecipeCard from '@/components/RecipeCard.vue'
import DropdownFilter from '@/components/DropdownFilter.vue'
import recipeData from '../data.json'
export default {
  name: 'Index',
  components: {
    RecipeCard,
    DropdownFilter,
  },
  data: () => ({
    search: '',
    recipes: recipeData,
    dropdownFilter: false,
  }),
  computed: {
    recipesFiltered() {
      return this.recipes.filter((recipe) => {
        return recipe.name.toLowerCase().includes(this.search.toLowerCase())
      })
    },
  },
}
</script>

<style lang="postcss">
.search-input {
  @apply rounded-lg bg-white px-2 py-2 shadow;
}
.search-input:focus {
  outline: 0;
  @apply shadow-outline;
}
.btn {
  @apply inline-block font-bold rounded-lg px-4 py-2 transition-colors duration-200;
}
.btn-circle {
  @apply inline-block font-bold rounded-full px-4 py-2 transition-colors duration-200 h-12 w-12;
}
.btn-orange {
  @apply bg-orange-400 text-white;
}
.btn-orange:hover {
  @apply bg-orange-500;
}
.list-enter-active,
.list-leave-active {
  transition: all 0.5s;
}
.list-enter,
.list-leave-to {
  opacity: 0;
}
.list-move {
  transition: transform 0.5s;
}

.fixed-bottom-right {
  @apply fixed;
  bottom: 20px;
  right: 40px;
}
</style>
