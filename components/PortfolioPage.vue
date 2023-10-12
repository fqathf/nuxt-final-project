<template>
  <div
    class="py-5 my-5 d-flex align-items-center flex-column justify-content-center"
  >
    <h1 class="border-bottom border-light">My Portfolio</h1>
    <div class="d-flex flex-row my-5">
      <a href="https://thisispalettes.vercel.app" target="_blank"
        ><div class="example">
          <img
            class="portfolio-img"
            src="../assets/palettes-ss.png"
            alt=""
          /></div
      ></a>
      <a
        href="https://www.freecodecamp.org/certification/fqathf/responsive-web-design"
        target="_blank"
        ><div class="example">
          <img
            class="portfolio-img"
            src="../assets/freecodecamp-rwd-certificate.jpg"
            alt=""
          /></div
      ></a>
      <a href="https://larvaz-nft.netlify.app" target="_blank"
        ><div class="example">
          <img
            class="portfolio-img"
            src="../assets/larvaz-ss.png"
            alt=""
          /></div
      ></a>
    </div>
    <NuxtLink to='portfolio'><button class="btn btn-secondary border border-danger">Show More</button></NuxtLink>
  </div>
</template>
<script>
export default {
  data() {
    return {
      portfolio: [] 
    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    async fetchData() {
      try {
        const result = await this.$axios.get("/rest/v1/portfolios", {
          headers: {
            "apikey": process.env.SUPABASE_KEY
            }
        })
        console.log(result)
        this.portfolio = result.data
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>
<style scoped>
.portfolio-img {
    width: 25vw;
    border: 5px #6a1313 solid;
}
</style>
