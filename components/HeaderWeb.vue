<template>
  <nav class="navbar navbar-expand-lg mx-0 px-0 d-flex justify-content-center">
    <div class="container row d-flex justify-content-center mx-0">
      <div
        class="px-5 col-12 col-md-6 d-flex justify-content-md-start justify-content-center"
      >
        <NuxtLink to="/"><button class="btn btn-danger bg-red border border-secondary">@fqathf</button></NuxtLink>
      </div>
      <div
        class="col-12 col-md-6 ml-md-5 d-flex justify-content-md-end justify-content-center"
      >
        <ul class="nav nav-pills d-flex text-center justify-content-center">
          <li
            class="nav-link py-0 px-4 border-right border-left border-danger rounded-0"
          >
            <NuxtLink class="nav-text text-light text-center" to="/">
              Beranda
            </NuxtLink>
          </li>
          <li class="nav-link py-0 px-4 border-right border-left border-danger rounded-0">
            <NuxtLink class="nav-text text-light text-center" to="/">
              Blog
            </NuxtLink>
          </li>
          <li class="nav-link py-0 px-4 border-right border-left border-danger rounded-0">
            <NuxtLink class="nav-text text-light text-center" to="/">
              Portfolio
            </NuxtLink>
          </li>
          <li
            class="nav-link py-0 px-4 border-right border-sm-top border-danger rounded-0"
          >
            <NuxtLink class="nav-text text-light text-center" to="/">
              About
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
<script>
export default {}
</script>
<style scoped>
.navbar {
  background: linear-gradient(
    180deg,
    rgba(217, 217, 217, 0.308) 0%,
    rgba(217, 217, 217, 0) 95%
  );
}
.nav-text {
  font-family: 'JetBrains Mono', monospace;
  font-weight: bolder;
  -webkit-text-stroke: 1px #6a1313;
  text-align: center;
  text-decoration: none;
  font-weight: 900;
}
@media (prefers-color-scheme: dark) {
  /* Dark theme styles go here */
  .navbar {
    background: linear-gradient(
      180deg,
      rgba(33, 33, 33, 0.7) 0%,
      rgba(33, 33, 33, 0) 95%
    );
  }
}
</style>
