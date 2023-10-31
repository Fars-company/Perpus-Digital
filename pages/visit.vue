<template>
  <div class="visit">
    <h1>VISIT LIST</h1>
    <NuxtLink to="/" class="btn">Isi Daftar Pengunjung</NuxtLink>
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
  background-color: #303e479a;
  height: 5000px;
  width: 100%;
}
h1{
  text-align: center;
  padding-top: 3%;
  color: white;
}
.btn{
  margin-top: 2%;
  width: 200px;
  height: 40px;
  background-color:rgb(95, 101, 109);
  color: white;
}
</style>