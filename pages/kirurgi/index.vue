<template>
  <div id="categories-page" class="page-wrapper categories-page">
    <site-hero title="Kirurgi" image="/uploads/home-hero.jpg" />
    <main-section theme="one-column">
      <categories-grid />
    </main-section>
  </div>
</template>
<script>
export default {
  head() {
    return {
      title: `Kirurgi | ${this.$siteConfig.siteName}`
    }
  }
}
</script>
