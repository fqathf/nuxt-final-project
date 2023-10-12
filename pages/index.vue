<template>
  <div id="main">
    <MainPage />
    <AboutPage />
    <PortfolioPage />
  </div>
</template>

<script>
export default {}
</script>
<style>
* {
  font-family: 'JetBrains Mono', monospace;
  margin: 0;
  padding: 0;
}
body {
  margin: 0;
  padding: 0;
  background-color: #d9d9d9;
}
.bg-red {
  background: #6a1313;
}
.text-stroke {
  -webkit-text-stroke: 1px #6a1313 ;
}

/* Dark/Light Theme */
@media (prefers-color-scheme: dark) {
    /* Dark theme styles go here */
    body {
        color: #eee;
        background: #212121;
    }
}
</style>
