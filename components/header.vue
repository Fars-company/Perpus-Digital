<template>
  <nav class="navbar navbar-expand-lg">
    <div class="container-fluid">
      <a class="navbar-brand d-flex flex-direction-row align-items-center" href="#"
        ><img src="~/assets/img/logo.png" alt="" />
        <h1>PERPUS DIGITAL</h1></a
      >
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav text-white ms-auto">
          <NuxtLink class="nav-link" to="/">HOME</NuxtLink>
          <NuxtLink class="nav-link" to="/visit">RIWAYAT KUNJUNGAN</NuxtLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<script lang="ts" setup></script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,600;1,500&family=Playpen+Sans:wght@700&display=swap");
.nav-link {
  color: white;
  font-size: 80%;
  padding-left: 3%;
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
}
h1 {
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
  color: white;
  margin-left: 5%;
}
.navbar {
  background-color: rgb(31, 86, 206);
  width: 100%;
}
img {
  width: 100px;
  margin-left: 5%;
}
/* 
@media (max-width=400px) {
  h1 {
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
  color: white;
  font-size: 20px;
}
} */
</style>
