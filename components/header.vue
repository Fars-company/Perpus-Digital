<template>
  <nav class="navbar navbar-expand-lg">
    <div class="container-fluid">
      <a class="navbar-brand" href="#"><img src="~/assets/img/logo.png" alt=""></a>
      <h1>PERPUSTAKAAN DIGITAL</h1>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav justify-content-flex-end">
          <NuxtLink class="nav-link" to="/visit">VISIT</NuxtLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<script lang="ts" setup>
</script>

<style scoped>
h1{
  color: white;
}
.navbar{
  background-color: rgb(31, 86, 206);
}
img {
  width: 100px;
  padding-left: 20%;
}
</style>