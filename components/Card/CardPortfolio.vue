<template>
  <div>
    <b-card
      :title="portfolio.title"
      :img-src="portfolio.photo"
      :article="portfolio"
      img-alt="Image"
      img-top
      tag="portfolio"
      style="max-width: 20rem"
      class="mb-2 text-dark"
    >
      <b-card-text>
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </b-card-text>

      <b-button :href="portfolio.url" target="_blank" variant="primary">Visit</b-button>
    </b-card>
  </div>
</template>
<script>
export default {
  props: {
    portfolio: {
      type: Object,
      default() {
        return {}
      }
    },
  },
  computed: {
    localTask: {
      get () {
        return this.portfolio
      },
      set (newValue) {
        this.$emit('update:portfolio', newValue)
      }
    }
  }
}
</script>