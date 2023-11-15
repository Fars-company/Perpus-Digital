<template>
  <div class="visit">
    <h1>RIWAYAT KUNJUNGAN</h1>
    <NuxtLink to="/" class="btn">Isi Daftar Pengunjung</NuxtLink>
    <div class="m-2">Menampilkan {{ visitors.length }} data</div>
      <table class="table">
        <thead class="table-primary table-bordered">
          <tr>
            <th>No</th>
            <th>Tanggal</th>
            <th>Nama</th>
            <th>Kategori</th>
            <th>Keperluan</th>
          </tr>
          </thead>
          <tbody class="table-bordered">
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
  .select()
  .order('tanggal',{ascending: false })
  if (data) visitors.value = data;
}

onMounted(() => getData());
</script>

<style scoped>
.table-bordered{
  width: 96%;
  margin-left: 2%;
  text-align: center;
}
.visit{
  background-color: #ffffff;
  width: 100%;
}
h1{
  text-align: center;
  padding-top: 3%;
  color: rgb(0, 0, 0);
}
.btn{
  margin: 2%;
  width: 200px;
  height: 40px;
  background-color: rgb(31, 86, 206);
  color: white;
}
</style>