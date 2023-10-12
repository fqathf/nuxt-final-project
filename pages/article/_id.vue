<template>
  <div class="py-4">
    <div class="container pt-5">
      <div v-for="article in articles" :key="article.id">
        <div v-if="article.id == paramId">
          <div class="container">
            <h1>{{ article.title }}</h1>
            <b-img
              class="rounded mx-auto d-block"
              style="width: 600px"
              fluid
              :src="article.img"
            ></b-img>
            <p class="mt-3 mx-3">{{ article.content }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      paramId: this.$route.params.id,
      articles: [],
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
