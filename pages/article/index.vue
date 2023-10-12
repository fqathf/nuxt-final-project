<template>
    <!--tampilan banyak blog-->
    <div class="container pt-5 row mx-5">
        <CardArticle 
            class="col-4 col-md-4"
            v-for="(article, i) in resultQuery"
            :key="i"
            :article="article"
        />
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
    }
  },
  computed: {
    resultQuery() {
      return this.articles
    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    async fetchData() {
      try {
        const result = await this.$axios.get("/rest/v1/articles", {
          headers: {
            "apikey": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZoa3RocHlvaGZ3aWZrZm11bGt2Iiwicm9sZSI6ImFub24iLCJpYXQiOjE2OTYyMTMyODMsImV4cCI6MjAxMTc4OTI4M30.JUjs83-uFpn9PpCAUwtt0Nvr9VN0LDmHlg6sIf1ErQc"
            }
        })
        console.log(result)
        this.articles = result.data
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>