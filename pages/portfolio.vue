<template>
  <!--tampilan banyak blog-->
  <div>
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
              process.env.SUPABASE_KEY
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
