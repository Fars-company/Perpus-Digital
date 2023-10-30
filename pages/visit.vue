<template>
  <div class="row">
    <div class="col">
      <div class="visit">
    <h1>VISIT LIST</h1>
    <NuxtLink to="/" class="btn">Isi Daftar Pengunjung</NuxtLink>
    <div class="row">
      <div class="col">
        <table class="table">
          <thead>
            <tr>
              <th>No</th>
              <th>Tanggal</th>
              <th>Nama</th>
              <th>Kategori</th>
              <th>Keperluan</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(kunjungan, index) in visitors" :key="kunjungan.id">
              <td>{{ index + 1 }}</td>
              <td>{{ kunjungan.tanggal }}</td>
              <td>{{ kunjungan.nama }}</td>
              <td>{{ kunjungan.kategori }}</td>
              <td>{{ kunjungan.keperluan }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
    </div>
  </div>
</template>
<script setup>
const supabase = useSupabaseClient();
const visitors = ref([]);

async function getData() {
  const { data, error } = await supabase
  .from("kunjungan")
  .select();
  if (data) visitors.value = data;
}

onMounted(() => getData());
</script>

<style scoped>
.visit{
  background-color: #273a489a;
  height: 600px;
  width: 100%;
}
h1{
  text-align: center;
  color: white;
}
.btn{
  margin-top: 2%;
  width: 200px;
  height: 40px;
  background-color: #99a9b3ad;
}
</style>