<template>
  <!--tampilan banyak blog-->
  <div class="pt-5 container">
    <b-form-input class="mt-5" v-model="search" placeholder="Search..."></b-form-input>
    <div class="container pt-5 row mx-5">
      <CardPortfolio
        class="col-4 col-md-4"
        v-for="(portfolio, i) in resultQuery"
        :key="i"
        :portfolio="portfolio"
      />
    </div>
  </div>
</template>
<script>
import CardPortfolio from '@/components/Card/CardPortfolio.vue'

export default {
  components: {
    CardPortfolio,
  },
  data() {
    return {
      portfolios: [],
      search: '',
    }
  },
  computed: {
    resultQuery() {
      return this.portfolios
    },
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    async fetchData() {
      try {
        const result = await this.$axios.get('/rest/v1/portfolios', {
          headers: {
            apikey:
              process.env.SUPABASE_ANON_KEY
            },
        })
        console.log(result)
        this.portfolios = result.data
      } catch (error) {
        console.log(error)
      }
    },
  },
}
</script>
