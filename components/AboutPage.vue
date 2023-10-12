<template>
  <div class="row bg-red col-12 py-5">
    <div id="about" class="col-12 col-md-6 px-3">
      <img src="" alt="" />
      <div>
        <h1 class="border-bottom border-light">About Me</h1>
        <p>
          I'm Faiq Athif, an 18-year-old individual with a passion for
          Information Technology and interest in Football.<br /><br />
          I just graduated from SMA Islam Cendekia Muda and continue my studies
          in Telkom University
        </p>
      </div>
    </div>
    <div id="blog" class="col-12 col-md-6 d-flex flex-column px-3">
      <h1 class="text-center border-bottom border-light">My Blog</h1>
      <div class="border border-secondary">
        <b-carousel
          id="carousel-fade"
          style="text-shadow: 0px 0px 2px #000"
          fade
          indicators
          img-width="1024"
          img-height="480"
        >
          <BlogSlide
            v-for="(article, i) in resultQuery"
            :key="i"
            :article="article"
          />
        </b-carousel>
      </div>
      <NuxtLink class="d-flex justify-content-center" to="/article"><button class="btn btn-secondary border border-danger">Visit Blog</button></NuxtLink>
    </div>
  </div>
</template>
<script>
import BlogSlide from '@/components/Slide/BlogSlide.vue'

export default {
  components: {
    BlogSlide,
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
