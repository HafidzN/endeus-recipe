<template>
  <main class="main">
    <section class="main__container leading-[1.15] box-border overflow-x-hidden pb-16 h-pt-70">
      <section class="main__collection-item leading-[1.15] box-border mt-16">
        <div class="leading-[1.15] box-borderpx-12">
          <h2 class="text-center box-border text-[22px] leading-[30px] text-[#323e48] font-bold tracking-[4px] uppercase m-0">Kategori Resep</h2>
        </div>
        <div class="main__menu-list leading-[1.15] box-border flex flex-wrap justify-center justify-items-center mt-2 -mx-2 my-0 px-4 py-0">
          <CategoryItem v-for="category in categories" :key="category.id"
            :category-title="category.title"
            :container-title="category.title"
            :category-link="category.link"
            :image-url="category.imgSrc"
            :image-alt="category.title"
            :image-width="100"
            :image-height="100" />   
        </div>
      </section>
    </section>
  </main>
</template>

<script>
import CategoryItem from '@/components/CategoryItem.vue'
import { computed } from 'vue'
import { useStore } from 'vuex'

export default {
  name: 'HomeView',
  components: {
    CategoryItem
  },
  setup () {
    const store = useStore()
    const categories = computed(() => store.state.categories.categories)
    return {
      categories
    }
  }
}
</script>

<style lang="scss" scoped>
.main__container {
  max-width: 1200px;
  margin: 0 auto;
  justify-content: space-between;
}

.h-pt-70 {
  padding-top: 70px;
}

@media (max-width: 767px) {
  .main {
    &__collection-item {
      margin-top: 32px;
    }
  }
}
</style>
