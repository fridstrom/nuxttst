<template>
  <div id="category-page" class="page-wrapper category-page">
    <site-hero
      :title="$store.state.name"
      :subtitle="$store.state.content"
      :image="$store.state.image"
    />
    <main-section theme="sidebar-right">
      <template v-slot:default>
        <!-- Posts in Category -->
        <posts-grid :category="[$store.state.name]" :per-row="2" />
      </template>
      <template v-slot:sidebar>
        <h3 class="subtitle">
          All CategoriesX
        </h3>
        <pre>{{ allCats }}</pre>
        <div class="panel">
          <nuxt-link
            v-for="cat in allCats"
            :key="cat.slug"
            :to="`/categories/${cat.slug}`"
            :class="{
              'panel-block': true,
              'is-active': cat.slug === $route.params.single
            }"
          >
            {{ cat.name }}
          </nuxt-link>
        </div>
      </template>
    </main-section>
  </div>
</template>
<script>
import { setPageData } from '../../helper'
export default {
  data() {
    return {
      allCats: []
    }
  },
  fetch({ store, params }) {
    setPageData(store, { resource: 'category', slug: params.single })
  },
  async created() {
    let tmpCat = await this.$cms.category.getAll();
    console.log("categories",tmpCat);
    this.allCats = tmpCat;
  }
}
</script>
