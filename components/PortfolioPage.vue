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
            "apikey": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZoa3RocHlvaGZ3aWZrZm11bGt2Iiwicm9sZSI6ImFub24iLCJpYXQiOjE2OTYyMTMyODMsImV4cCI6MjAxMTc4OTI4M30.JUjs83-uFpn9PpCAUwtt0Nvr9VN0LDmHlg6sIf1ErQc"
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
