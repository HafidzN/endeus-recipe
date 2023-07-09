<template>
  <main class="menus">
    <section class="menus__container leading-[1.15] box-border overflow-x-hidden pb-16 h-pt-70">
      <section class="menus__collection-item leading-[1.15] box-border mt-16">
        <div class="leading-[1.15] box-border text-center text-[#7d8ca3] my-9 px-4">
          <h1 class="text-center box-border font-medium text-3xl leading-8 text-[#231f20] m-0 p-0 capitalize">{{currentCategory}}</h1>
        </div>
        <div class="menus__main leading-[1.15] box-border m-auto pb-6 px-4">
        <div class="menus__gallery">
            <div class="menus__item" v-for="recipe in recipes" :key="recipe.id">
                <RecipeItem 
                    :title="recipe.title"
                    :imgSrc="recipe.imgSrc"
                    :hasVideo="recipe.hasVideo"
                    :duration="recipe.duration"
                    :id="recipe.id"
                />
            </div>
        </div>
        </div>
      </section>
    </section>
  </main>
</template>

<script>
import RecipeItem from '@/components/RecipeItem.vue'
import { computed } from 'vue'
import { useStore } from 'vuex'
import { useRoute } from 'vue-router'

export default {
  name: 'CategoryView',
  components: {
    RecipeItem
  },
  setup () {
    const store = useStore()
    const route = useRoute()
    const categoryParam = route.params.category

    const filteredRecipes = computed(() => {
      return store.getters['recipes/getFilteredRecipes'](categoryParam)
    })


    return {
        recipes: filteredRecipes,
        currentCategory: categoryParam.replace(/-/g, ' ')
    }
  }
}
</script>

<style lang="scss" scoped>
.menus__container {
  max-width: 1200px;
  margin: 0 auto;
  justify-content: space-between;
}

.menus__gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-gap: 30px;
}

.h-pt-70 {
    padding-top: 70px
}

@media (max-width: 800px) {
  .menus__gallery {
    grid-template-columns: repeat(2, 1fr);
  }
  .menus__item:nth-child(5n + 1){
    grid-column: 1 / -1;
  }
}

@media (max-width: 800px) {
  .menus__gallery {
    grid-gap: 18px;
  }

 .menus__item:nth-child(5n + 1){
    grid-column: 1 / -1;
  }
}

@media (min-width: 801px) {
  .menus__gallery {
    grid-template-columns: repeat(4, 1fr);
  }
}   

@media (max-width: 767px) {
  .menus {
    &__collection-item {
      margin-top: 32px;
    }
  }
}
</style>
