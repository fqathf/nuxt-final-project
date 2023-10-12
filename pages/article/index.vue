<template>
  <!--tampilan banyak blog-->
  <div class="pt-5 container">
    <b-form-input class="mt-5" v-model="search" placeholder="Search..."></b-form-input>
    <div class="container pt-5 row mx-5">
      <CardArticle
        class="col-4 col-md-4"
        v-for="(article, i) in resultQuery"
        :key="i"
        :article="article"
      />
    </div>
  </div>
</template>
<script>
import CardArticle from '@/components/Card/CardArticle.vue'

export default {
  components: {
    CardArticle,
  },
  data() {
    return {
      articles: [],
      search: '',
    }
  },
  computed: {
    resultQuery() {
      return this.articles
    },
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    async fetchData() {
      try {
        const result = await this.$axios.get('/rest/v1/articles', {
          headers: {
            apikey: process.env.SUPABASE_ANON_KEY,
          },
        })
        console.log(result)
        this.articles = result.data
      } catch (error) {
        console.log(error)
      }
    },
  },
}
</script>
