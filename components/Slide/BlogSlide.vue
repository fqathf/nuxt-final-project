<template>
  <NuxtLink :to="'article/' + article.id">
    <b-carousel-slide
      :caption="article.title"
      :img-src="article.img"
      :article="article"
    ></b-carousel-slide>
  </NuxtLink>
</template>
<script>
export default {
  props: {
    article: {
      type: Object,
      default() {
        return {}
      }
    },
  },
  computed: {
    localTask: {
      get () {
        return this.article
      },
      set (newValue) {
        this.$emit('update:article', newValue)
      }
    }
  }
}
</script>