<template>
  <div>
    <b-card
      :title="portfolio.title"
      :img-src="photo[0]"
      :article="portfolio"
      img-alt="Image"
      img-top
      tag="portfolio"
      style="max-width: 20rem"
      class="mb-2 text-dark"
    >
      <b-card-text>
        Utilized: {{ portfolio.tech }}
      </b-card-text>
      <b-button variant="info" v-b-modal="portfolio.id">Detail</b-button>
      <b-button v-if="portfolio.url" :href="portfolio.url" target="_blank" variant="primary">Visit</b-button>
      
      <ModalPortfolio :photo="photo" :portfolio="portfolio"/>
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
  data() {
    return {
      photo: this.portfolio.photo ? this.portfolio.photo.split(',') : [],
    }
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