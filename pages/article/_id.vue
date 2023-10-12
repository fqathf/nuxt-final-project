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
            "apikey": process.env.SUPABASE_ANON_KEY
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
