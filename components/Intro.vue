<template>
  <div class="intro">
    <div class="layer">
      <h1 class="text-center">SELAMAT DATANG DI PERPUSTAKAAN DIGITAL</h1>
      <h3>SMKN 4 TASIKMALAYA</h3>
    </div>
  </div>
</template>


<style scoped>
.intro {
  width: 100%;
  height: 600px;
  display: table;
  background: transparent url("@/assets/img/foto.png") no-repeat center center;
  background-size: cover;
}

.intro .text-center {
  padding-top: 20%;
}

.intro .inner-intro {
  z-index: 1;
}

.intro .layer {
  width: 100%;
  height: 600px;
  background-color: #ffffff;
  opacity: 0.8;
  z-index: -1;
}

h3 {
  text-align: center;
}
</style>