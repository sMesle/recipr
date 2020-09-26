<template>
  <div>
    <card title="Creation d'une recette">
      <div class="max-w-md mx-auto">
        <form-input
          v-model="recipe.title"
          label="Titre"
          placeholder="Donner un nom à la recette"
          bold-label
        />
        <div class="bold-label">Ingrédients</div>
        <div v-if="recipe.ingredients.length > 0" class="mb-4">
          <div v-for="(ing, i) in recipe.ingredients" :key="'ing_' + i">
            <div class="flex mb-2">
              <span class="font-bold"
                >{{ ing.quantity }}{{ ing.unit }}&nbsp;</span
              >
              <span>{{ ing.name }}</span>
            </div>
          </div>
        </div>
        <input
          v-model="ingredient"
          placeholder="Entrer un ingrédient"
          class="form-input"
          @keyup.enter="addIngredient"
        />
      </div>
      <div class="flex justify-end">
        <button class="btn btn-orange">Créer</button>
      </div>
    </card>
  </div>
</template>

<script>
export default {
  name: 'RecipeCreation',
  data: () => ({
    recipe: {
      title: '',
      ingredients: [],
    },
    ingredient: '',
  }),
  methods: {
    addIngredient() {
      if (this.ingredient !== '') {
        // split string into array
        const splited = this.ingredient.split(' ')
        // Get unite (remove number from 1st array)
        const unit = splited[0].replace(/[0-9]/g, '')
        // Remove first element
        splited.shift()
        // Join rest of the table to get the name
        const name = splited.join(' ')
        // Get quantity
        const quantity = parseInt(this.ingredient, 10)
        const data = {
          quantity,
          unit,
          name,
        }
        this.recipe.ingredients.push(data)
        this.ingredient = ''
      }
    },
  },
}
</script>

<style lang="postcss">
.form-control {
  @apply border border-gray-500 rounded-lg px-3 py-1;
}
.form-control:focus {
  outline: 0;
}
.btn {
  @apply inline-block font-bold rounded-lg px-4 py-2 transition-colors duration-200;
}
.btn-orange {
  @apply bg-orange-400 text-white;
}

.form-input {
  @apply border border-gray-300 rounded-lg px-3 py-2 mb-6 w-full transition duration-200;
}
.form-input:hover {
  @apply border-gray-500;
}
.form-input:focus {
  @apply border-orange-400;
  outline: 0;
}
</style>
