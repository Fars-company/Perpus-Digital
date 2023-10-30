<template>
  <div class="row my-3">
    <nav class="navbar navbar-expand-lg bg-secondary">
  <div class="container-fluid">
    <a class="navbar-brand" href="#"><img src="~/assets/img/logo.png" alt=""></a>
    <h1>DIGITAL LIBRARY</h1>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
      <div class="navbar-nav justify-content-flex-end">
        <a class="nav-link active" aria-current="page" href="#">HOME</a>
        <NuxtLink class="nav-link" to="/visit">VISIT</NuxtLink>
      </div>
    </div>
  </div>
</nav>
  </div>
</template>

<script lang="ts" setup>
</script>

<style scoped>
img {
  width: 100px;
  padding-left: 20%;
}
</style>