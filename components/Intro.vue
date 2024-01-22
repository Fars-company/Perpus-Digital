<template>
  <div class="intro">
    <marquee scrollamount="20" class="layer">
      <h1 class="text-center">SELAMAT DATANG DI PERPUSTAKAAN DIGITAL</h1>
      <h3>SMKN 4 TASIKMALAYA</h3>
    </marquee>
  </div>
</template>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,600;1,500&family=Playpen+Sans:wght@700&display=swap');
.intro {
  width: 100%;
  height: 600px;
  background: transparent url("@/assets/img/foto.png") no-repeat center center;
  background-size: cover;
}

.intro .text-center {
  padding-top: 20%;
  font-family: 'Josefin Sans', sans-serif;
  font-family: 'Playpen Sans', cursive;
}

.intro .inner-intro {
  z-index: 1;
}

.intro .layer {
  width: 100%;
  height: 620px;
  background-color: #ffffff;
  opacity: 0.8;
  z-index: -1;
}

h3 {
  text-align: center;
  font-family: 'Josefin Sans', sans-serif;
  font-family: 'Playpen Sans', cursive;
}
</style>